# Download and Usage Instructions

This page describes the current authorized server route and a draft future AWS
route. Replace placeholders only after the public repository is configured.

## Metadata workbook

```text
metadata/metadata.xlsx
```

The workbook contains 13,933 records. For the image-only release, exclude the
two rows with `plate_well_status=final_figure`, leaving 13,931 TIFF records.

Example:

```python
import pandas as pd

images = pd.read_excel("metadata/metadata.xlsx", sheet_name="images")
images = images[images["plate_well_status"] != "final_figure"]

raw_images = images[images["image_role"] == "raw_whole_well"]
single_worm_16bit = images[
    images["image_role"] == "single_worm_crop_input"
]
single_worm_8bit = images[
    images["image_role"] == "processed_single_worm_output"
]
```

For paired-modality reuse, retain only acquisition keys containing both `w1`
and `w2`. Do not treat `w2` as a second fluorescence channel; it is transmitted
light in this dataset.

## Future public AWS access

```bash
aws s3 sync --no-sign-request \
  s3://<bucket-name>/<optional-prefix>/C_elegans_COL12_Collagen_Secretion_Dataset/<screening-data-prefix>/ \
  ./C_elegans_COL12_Collagen_Secretion_Dataset/<screening-data-prefix>/
```


See [Data Structure](COL12_data_structure.md) before reorganizing source folders and
[Screening Image Workflow](COL12_screening_workflow.md) before reusing the
single-worm derivatives.
