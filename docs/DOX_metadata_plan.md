# Metadata

The current metadata file is:

```text
metadata/metadata.xlsx
```

This workbook contains one sheet, `Sheet1`, with 3,329 data rows. Each row
represents one imaging file included in the curated database. The source
archive contains 3,427 files; 98 files are excluded under the curation rules
below. The workbook follows the column structure of the ZF_APOC2 metadata
template:

- source-computer absolute paths are not included
- dataset-relative paths are used
- a stable `image_id` column is included
- exact file sizes from the remote inventory are recorded
- unresolved technical fields are flagged rather than guessed

The numbered-compound lookup is distributed separately as:

```text
metadata/compound_plate_map.xlsx
```

This plate map uses English-first delivery columns: `compound_number`,
`compound_name_english`, `compound_name_chinese`, `cas_number`, and
`mapping_status`. English names were matched by the source CAS number where
possible, while the source Chinese name is retained for traceability. The
compound number is used to interpret numbered filenames without duplicating
the same lookup across all image-manifest rows. For example, `350-1.tiff` maps
to compound 350, cyanidin chloride (`氯化矢车菊素`; CAS 528-58-5), replicate 1.

The source plate list contains entries numbered 1–351 but has no record for
compound 346. CAS numbers are absent for compounds 238 and 297. Compound 238
is translated directly from its source name as Gypenoside XVIII. The English
name for compound 270 could not be verified against its source CAS, and the
English name for compound 297 remains unresolved because both a reliable
translation and CAS identifier are unavailable. These limitations are recorded
in `mapping_status` rather than inferred.

## Current Metadata Columns

| Column | Description |
|---|---|
| `image_id` | Stable generated file identifier |
| `relative_path` | Path relative to the remote `dox` dataset root |
| `file_name` | Original filename |
| `file_format` | Lowercase file extension |
| `resolution_or_frames` | Resolution and frame count where recoverable from verified recurring stack patterns |
| `color_type` | Image color mode, such as `grayscale` |
| `bit_depth` | Image bit depth where currently supported by representative-file inspection |
| `contrast_std` | Standard deviation of pixel intensity, used as a simple image-contrast indicator; this should be computed automatically and is currently uncomputed |
| `size_kb` | Exact remote file size converted to KiB |
| `fluorescence_type` | Imaging/channel description where applicable |
| `object_type` | Biological object, currently `zebrafish` for imaging records |
| `dataset_description` | Dataset-level description recorded in the first data row |
| `metadata_issue` | File-level limitations or fields requiring automatic extraction or manual confirmation |

## Naming Conventions Used for Curation

- Top-level date or date-time folders identify acquisition/experiment batches.
- Numbered screening names use compound-library number followed by fish or
  replicate number; for example, `350-1` denotes compound 350, replicate 1.
- Numbered compound identities should be resolved against
  `metadata/compound_plate_map.xlsx`.
- Named treatments generally follow a treatment-dose-fish pattern.
- `M-30-1-1` denotes model group, 30 h modeling, fish 1, extra view 1.
- `C` and `Con` denote controls; `M` denotes the model group; `DXZ` and `YANG`
  denote dexrazoxane; `XI` denotes hours.
- `dxz-n` is handled as an ordinary DXZ replicate.

The treatment codebook is recorded in the `dataset_description` field and in
[Data Structure](DOX_data_structure.md). Original filenames and relative paths are
not normalized or rewritten.

## Exclusion Rules

The metadata excludes 98 source-archive files: 31 display images, 27
statistical or derived outputs, 2 dead-specimen files, 5 unresolved `Z` files,
32 unresolved `mei` files, and 1 non-image support file. Files marked `jixing`
and `XUELIU` remain included and are identified in `metadata_issue` as
deformed/abnormal-phenotype and blood-flow images, respectively.
