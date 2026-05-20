# Metadata

The current metadata file is:

```text
metadata/metadata.xlsx
```

This workbook contains one sheet, `images`, with 1,878 rows. Each row represents
one image in the current dataset package. The file has been cleaned for public
documentation:

- source computer absolute paths were removed
- dataset-relative paths are used instead
- a stable `image_id` column was added
- the previously missing path for `apoc2mutant- (1).JPG` was corrected

## Current Metadata Columns

| Column | Description |
|---|---|
| `image_id` | Stable generated image identifier |
| `relative_path` | Path relative to the dataset root |
| `file_name` | Original image filename |
| `file_format` | Image file format, such as `tif` or `jpg` |
| `resolution_or_frames` | Image resolution or frame information |
| `color_type` | Color mode, such as grayscale or color |
| `bit_depth` | Image bit depth |
| `contrast_std` | Image contrast standard deviation |
| `size_kb` | File size in KB |
| `fluorescence_type` | Imaging/channel type, currently `FITC` or `TL` |
| `object_type` | Object type, currently zebrafish |
| `dataset_description` | Section-level description text |
| `metadata_issue` | Flags rows that need manual correction |

