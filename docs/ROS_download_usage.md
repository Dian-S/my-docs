# Download and Usage Instructions

This page describes the current authorized server route and a draft future AWS
route. `<screening-data-prefix>` represents the physical source subdirectory;
replace it with the final public prefix when the package is deposited.

## Metadata workbook

```text
metadata/metadata.xlsx
```

The current `images` sheet contains 13,273 records. For the image-only release,
filter out the two records with `plate_well_status=final_figure`, leaving
13,271 screening-image records. Use:

- `image_id` as the stable record key;
- `relative_path` to resolve the file from the dataset root;
- `plate_id + well_id` for plate-based joins; and
- `library_index`, `targetmol_id`, `compound_name`, and `cas_number` for
  compound annotation when `plate_well_status=compound_mapped`.

Example:

```python
import pandas as pd

images = pd.read_excel("metadata/metadata.xlsx", sheet_name="images")
images = images[images["plate_well_status"] != "final_figure"]
raw_plate_images = images[
    images["relative_path"].str.contains("/raw_data/")
    & ~images["relative_path"].str.contains("/single_worm_data_7.8/")
    & images["file_format"].eq("tif")
]
```

For paired-channel analysis, construct a plate/well key and retain only keys
containing both `FITC` and `DAPI` records:

```python
raw_plate_images = raw_plate_images.assign(
    plate_well_key=
        raw_plate_images["plate_id"].astype(str)
        + "|"
        + raw_plate_images["well_id"].astype(str)
)

channel_sets = raw_plate_images.groupby("plate_well_key")[
    "fluorescence_type"
].agg(set)
paired_keys = channel_sets[channel_sets.apply(
    lambda channels: {"FITC", "DAPI"}.issubset(channels)
)].index

paired_raw_images = raw_plate_images[
    raw_plate_images["plate_well_key"].isin(paired_keys)
]
```
## Future public AWS access

```bash
aws s3 sync --no-sign-request \
  s3://<bucket-name>/<optional-prefix>/C_elegans_ROS_Dataset/<screening-data-prefix>/ \
  ./C_elegans_ROS_Dataset/<screening-data-prefix>/
```

See [Scellseg Single-Worm Image Processing](ROS_tools_README.md) before
reusing derived single-worm images or attempting to reproduce segmentation.

The supporting software is distributed as `scellseg_analysis/` and
`scellseg_analysis.zip`. Setup, commands, expected outputs, and unresolved
project parameters are provided in the
[Scellseg Analysis Workflow](ROS_scellseg_analysis_workflow.md).
