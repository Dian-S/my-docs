# Metadata

## Delivered workbook

```text
metadata/metadata.xlsx
```

The workbook contains one `images` sheet with 13,933 records and 30 fields.
The intended screening-image release contains 13,931 TIFF records.

## Coverage

| Image group | Records |
|---|---:|
| Raw whole-well TIFFs | 2,186 |
| 16-bit single-worm TIFFs | 4,718 |
| 8-bit single-worm TIFFs | 7,027 |
| **Screening images retained for release** | **13,931** |
| **Current workbook total** | **13,933** |

## Core image schema

| Field | Definition |
|---|---|
| `image_id` | Stable dataset-local image identifier |
| `relative_path` | File path relative to the dataset root |
| `file_name` | Distributed filename |
| `file_format` | Lowercase extension without a leading dot |
| `resolution_or_frames` | Pixel dimensions or frame information |
| `color_type` | `grayscale` |
| `bit_depth` | Pixel bit depth |
| `contrast_std` | Descriptive pixel-intensity standard deviation |
| `size_kb` | Remote byte size converted to KiB |
| `fluorescence_type` | `FITC/GFP`, `TL`|
| `object_type` | `C. elegans` |
| `dataset_description` | Row-level description of image role |
| `metadata_issue` | Record-specific uncertainty or provenance warning |

## Compound annotation

| Field | Definition |
|---|---|
| `plate_id` | Original L6000 library plate when confirmed |
| `well_id` | Original L6000 library well when confirmed |
| `library_index` | L6000 sequential index |
| `targetmol_id` | TargetMol identifier |
| `compound_name` | L6000 compound name; `Con` for documented controls |
| `cas_number` | CAS registry number from L6000 |
| `plate_well_status` | Mapping state: compound, control, unassigned |

## Processing and provenance fields

| Field | Definition |
|---|---|
| `image_role` | Raw whole-well, 16-bit crop, 8-bit output |
| `processing_level` | `raw`, `processed` |
| `acquisition_date` | Date parsed from the acquisition path or filename |
| `acquisition_batch` | Source acquisition or processing directory |
| `acquisition_plate_label` | Plate label encoded in the source tree |
| `acquisition_well_id` | Well encoded in the filename |
| `mapping_basis` | Evidence used for compound or control assignment |
| `screening_inclusion` | Relationship to the 614-row screening table |
| `screening_hit_status` | Candidate, control, non-selected, analysis-only, or unresolved status |
| `figure_association` | Link to the source publication/material represented by the record |

## Raw modality-pair QC

The 2,186 raw TIFFs represent 1,099 acquisition positions:

- 1,087 positions contain both `w1` FITC/GFP and `w2` transmitted light;
- 11 contain only `w2`;
- one contains only `w1`; and
- no duplicate acquisition-key/channel files were identified.

Incomplete pairs may remain useful for single-channel review but must be
identified explicitly in workflows requiring both modalities.

## Mapping status

| Status | Image records | Interpretation |
|---|---:|---|
| `compound_mapped` | 11,283 | Plate and well support an L6000 compound assignment |
| `control` | 878 | Control assignment supported by processing-layout workbooks |
| `unassigned` | 1,770 | Original library compound cannot be confirmed |

The mapped records represent 572 unique original L6000 plate-and-well keys.
This count is not expected to equal the 614 screening-table rows because the
archive contains repeated/re-imaged acquisitions and unresolved complement
positions, while some final-table entries do not map cleanly to the available
library workbook.

## Mapping and curation rules

1. Direct plate filenames are parsed to plate and well and joined to the L6000
   compound list.
2. The 614 screening records are taken from `final-plotting.xlsx`: 299 records
   in the plate-group 1/3/7/8 list and 315 in the plate-group 2/4/5/6 list.
3. The 26 published candidates are matched by CAS number where possible.
4. Vitamin A is marked as the positive control.
5. Tetracycline hydrochloride is marked as analysis-only because it appears in
   the supporting workbook but not in the publication's 26-compound list.
6. The complement/re-array label is not treated as an original L6000 plate.
   Only positions supported by independent candidate evidence are mapped.
7. Control assignments are based on processing-layout sheets; vehicle
   composition remains unknown.

## Interpretation boundary

This workbook is an image inventory. It does not contain the final normalized
mean-gray value used for compound comparison. `contrast_std` is an image
statistic, not the biological screening readout. Image-row counts also do not
equal compound count, well count, or biological replicate count.
