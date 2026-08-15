# Metadata

The current image-level metadata file is:

```text
metadata/metadata.xlsx
```

The workbook contains one sheet, `Sheet1`, with 1,219 data rows. Each row represents one zebrafish drug-screening image. 


## Current metadata columns

| Column | Description |
|---|---|
| `image_id` | Stable generated image identifier, such as `TPEN_SCREEN_000001` |
| `relative_path` | Image path relative to the TPEN dataset root |
| `file_name` | Current image filename |
| `file_format` | Image file format: `sif`, `tif`, or `tiff` |
| `resolution_or_frames` | Recorded image resolution or frame information |
| `color_type` | Image color mode; currently `grayscale` |
| `bit_depth` | Recorded bit depth: `8-bit`, `16-bit`, or `float32` |
| `contrast_std` | Image contrast standard deviation inherited from the reconciled source metadata |
| `size_kb` | Current remote file size in KB |
| `fluorescence_type` | Imaging/channel annotation; currently `FITC` |
| `object_type` | Biological object; currently `zebrafish` |
| `dataset_description` | Dataset-level description, populated once at the beginning of the sheet |
| `metadata_issue` | Image-level issue flag; currently blank for all 1,219 reconciled records |

## Current metadata summary

| Field | Current values |
|---|---|
| Images | 1,219 |
| Formats | 575 SIF, 490 TIF, 154 TIFF |
| Resolution | 920 at 640 × 540; 299 at 853 × 720 |
| Color type | 1,219 grayscale |
| Bit depth | 634 8-bit; 10 16-bit; 575 float32 |
| Fluorescence annotation | 1,219 FITC |
| Object type | 1,219 zebrafish |

## Compound reference

The treatment lookup file is:

```text
metadata/TPEN_compound_reference.xlsx
```

It contains three sheets:

| Sheet | Purpose |
|---|---|
| `compound_id_map` | Compound-number lookup transcribed from the supplied source table |
| `screening_name_legend` | Batch-level interpretation of treatment labels found in image filenames, including image counts |
| `notes` | Scope, source, and mapping notes |

Numeric compound identifiers are useful lookup keys but are not required when a treatment is identifiable by name. The treatment legend therefore accepts both identifier-based and name-based mappings. Examples include:

- `ZN`: zinc, recorded as a ZnSO4 positive rescue control.
- `GXN`: Guanxinning.
- `I`: probable abbreviation for Senkyunolide I, supported by Supplementary Table S1 and the supplied compound table.
- `RB1`: Ginsenoside Rb1.
- Rosmarinic acid: retained by name even though the supplied source row lacks a numeric ID.

Chinese compound names may be retained in the reference workbook as supplementary cross-references. Public-facing treatment names and the main image metadata should use English as the primary language.

## Recommended experiment-level additions

The current 13-column workbook is a complete image inventory, but future releases would benefit from structured treatment fields. These additions should be populated only when they can be verified from filenames, batch records, or laboratory documentation.

| Recommended field | Purpose |
|---|---|
| `screening_batch` | Normalized batch name: `3-4`, `3.13_screening`, `3.19_screening`, or `4.6` |
| `image_role` | Source/raw image or TIFF export |
| `treatment_label_raw` | Treatment label exactly as encoded in the filename |
| `treatment_name` | Normalized English compound or control name |
| `compound_id` | Optional source-table identifier; blank is acceptable for name-resolved treatments |
| `treatment_role` | Control, TPEN model, positive rescue control, screening compound, or screening medicine |
| `dose_value` | Numeric dose parsed or verified for the treatment |
| `dose_unit` | Dose unit verified from the experimental record; do not infer from the filename alone |
| `biological_replicate_id` | Biological-replicate number parsed from the final filename suffix; for example, `47-1` represents compound 47 and biological replicate 1 |
| `developmental_stage` | 2.5 dpf at treatment, with imaging 12 h later, where applicable |
| `TPEN_concentration_uM` | TPEN concentration; reported as 150 uM for the primary screen |
| `source_publication` | Article or DOI associated with the screening dataset |
| `source_image_id` | Link between an SIF source image and any TIFF-derived representation, if confirmed |

