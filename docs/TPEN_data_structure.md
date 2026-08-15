# Data Structure

## Top-level layout

The screening directory itself is treated as the dataset root for public metadata and documentation:

```text
TPEN_Drug_Screening_Dataset/
├── 3-4/
│   ├── gray/
│   ├── raw_images/
│   └── tif/
├── 3.13_screening/
│   ├── gray/
│   └── raw_images/
├── 3.19_screening/
│   ├── GRAY/
│   └── raw_images/
└── 4.6/
    ├── gray/
    └── raw_images/
```

## Batch summary

| Batch | Image files | Approx. size | Formats |
|---|---:|---:|---|
| `3-4` | 308 | 211.48 MB | 106 SIF, 202 TIF |
| `3.13_screening` | 353 | 494.95 MB | 183 SIF, 170 TIF |
| `3.19_screening` | 311 | 259.33 MB | 157 SIF, 154 TIFF |
| `4.6` | 247 | 210.21 MB | 129 SIF, 118 TIF |
| **Total** | **1,219** | **1,175.96 MB** | **575 SIF, 490 TIF, 154 TIFF** |

## Folder-level detail

| Folder | Files | Approx. size |
|---|---:|---:|
| `3-4/gray` | 101 | 37.25 MB |
| `3-4/raw_images` | 106 | 140.14 MB |
| `3-4/tif` | 101 | 34.10 MB |
| `3.13_screening/gray` | 170 | 94.22 MB |
| `3.13_screening/raw_images` | 183 | 400.73 MB |
| `3.19_screening/GRAY` | 154 | 51.77 MB |
| `3.19_screening/raw_images` | 157 | 207.56 MB |
| `4.6/gray` | 118 | 39.66 MB |
| `4.6/raw_images` | 129 | 170.54 MB |

## Directory-role notes

### `raw_images`

These folders contain Andor `.sif` microscopy files. The metadata records these images as float32 grayscale data. They should be treated as source microscopy files unless laboratory records indicate otherwise.

### `gray` and `GRAY`

These folders contain grayscale TIFF exports. The capitalization difference between `gray` and `GRAY` is part of the current remote directory structure and is preserved in `relative_path`.

### `tif`

The `3-4/tif` folder contains TIFF images associated with the corresponding screening batch. Any exact source-to-export pairing should be established using verified filename matching before being represented as a formal relationship.

## File naming notes

Filenames encode treatment and replicate information but are not fully standardized. Common patterns include:

- Numeric compound identifiers followed by a biological-replicate number. For example, `47-1` means compound 47, biological replicate 1, and `171-3` means compound 171, biological replicate 3. Equivalent filenames may use a space or underscore instead of a hyphen, such as `47 1` or `47_1`.
- Named compounds, such as `Curcumin`, `Hydroxysafflor_Yellow_A`, or `Ligustrazine`.
- Dose-like suffixes, such as `-50`, `-100`, or `-200`.
- Biological-replicate numbers appended with a space, underscore, or hyphen. The final replicate suffix should be stored separately from the compound identifier when filenames are parsed.
- Control labels, including `control`, `ctrl`, `CTRL`, or `c`.
- TPEN model labels, including `TPEN`, `tpen`, or `m`.
- Zinc rescue label `ZN`.
- Abbreviated or medicine labels, including `I`, `GXN`, and `RB1`.

The separate [`metadata/TPEN_compound_reference.xlsx`](metadata/TPEN_compound_reference.xlsx) workbook normalizes these filename labels. Missing numeric identifiers are acceptable when a treatment can be resolved by name.

## Metadata-to-file relationship

Every included image has one corresponding row in [`metadata/metadata.xlsx`](metadata/TPEN_metadata.xlsx).
The compound reference is available as
[`metadata/TPEN_compound_reference.xlsx`](metadata/TPEN_compound_reference.xlsx).

```text
image file
  ↕ matched by current dataset-relative path
metadata/metadata.xlsx row
  ↕ treatment label interpreted by batch and filename
metadata/TPEN_compound_reference.xlsx
```

The current metadata contains no rows for excluded Excel, Prism, temporary, or statistical-processing files.
