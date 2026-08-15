# Metadata

## Delivered workbook

[`metadata/metadata.xlsx`](metadata/ROS_metadata.xlsx)

The current workbook contains one `images` sheet with 13,273 records and 20
fields. The intended image-only release contains 13,271 records. The two
records with `plate_well_status=final_figure` are retained temporarily in the
workbook but are marked for exclusion when metadata is next revised.

## Image-level schema

| Field | Definition |
|---|---|
| `image_id` | Stable identifier, `CE_ROS_SCREEN_000001` to `CE_ROS_SCREEN_013273` |
| `relative_path` | File path relative to the dataset root |
| `file_name` | Distributed filename |
| `file_format` | Lowercase extension without a leading dot |
| `resolution_or_frames` | Pixel dimensions or frame information |
| `color_type` | `grayscale` or `color` |
| `bit_depth` | Pixel bit depth |
| `contrast_std` | Descriptive pixel-intensity standard deviation |
| `size_kb` | Remote byte size converted to KiB |
| `fluorescence_type` | Source channel or modality, such as `FITC`, `DAPI`, or `derived/composite` |
| `object_type` | `C. elegans` or `figure` |
| `dataset_description` | Screening and image-processing description inherited from source curation |
| `metadata_issue` | Record-specific provenance or unresolved limitation |
| `plate_id` | Canonical plate identifier, for example `PLATE 003` |
| `well_id` | Canonical 96-well position, for example `A02` |
| `library_index` | L6000 sequential library index |
| `targetmol_id` | TargetMol identifier |
| `compound_name` | L6000 compound name; `Con` for documented controls |
| `cas_number` | CAS registry number from the L6000 workbook |
| `plate_well_status` | `compound_mapped`, `control`, `unassigned`, or `final_figure` |

## Coverage

| Image group | Records |
|---|---:|
| Raw plate/well TIFFs | 1,409 |
| Scellseg-derived TIFFs | 10,458 |
| Scellseg/processing PNGs | 1,404 |
| Screening images retained for release | 13,271 |
| Final composite PNGs to exclude | 2 |
| **Current workbook total** | **13,273** |

### Whole-well channel-pair QC

The 1,409 raw TIFF files represent 709 unique plate/well positions:

- 700 positions have one `w1` and one `w2` image;
- seven positions contain only `w2`;
- two positions contain only `w1`; 
- no duplicate plate/well/channel files were identified in this group.

`w1` denotes the FITC/GFP channel and `w2` the DAPI/Violet channel; neither is
a transmitted-light (`TL`) image. The nine incomplete pairs remain in the
current inventory. Before release or analysis, they should either be retained
with an explicit missing-channel flag or excluded from paired-channel ratio
calculations.

## Mapping status

| Status | Image records | Interpretation |
|---|---:|---|
| `compound_mapped` | 10,664 | `plate_id + well_id` matches an L6000 compound entry |
| `control` | 2,422 | Column 1 or 12, labelled as control in the experimental layout |
| `unassigned` | 185 | Parseable internal position without a confirmed compound assignment |
| `final_figure` | 2 | Out-of-scope composite PNG; exclude from the public image release |

The workbook represents 582 unique mapped compound wells. The L6000 reference
contains 623 compound entries, whereas the experiment is reported as a
591-compound screen. These numbers are retained as distinct source facts; they
are not forced into agreement by assigning uncertain wells.

## Provenance and curation decisions

- Existing manually curated image properties were preserved where available.
- Windows absolute paths were replaced with verified dataset-relative paths.
- Plate and well identifiers were parsed from filenames and joined to the
  L6000 workbook using `plate_id + well_id`.
- Columns 1 and 12 were set to `compound_name=Con` and
  `plate_well_status=control`; no `Model` wells were inferred.
- Two final composite PNGs previously added from the directory snapshot are
  now designated for exclusion; the workbook is intentionally unchanged in
  the current documentation-only revision.
- Unresolved internal positions were retained as `unassigned` so that they can
  later be corrected or excluded without rewriting confirmed records.

## Interpretation boundary

This workbook is an image inventory. It does not contain the final normalized
`YFP500/YFP420` assay value used in primary-screen and candidate-comparison
analyses. `contrast_std` is an image statistic and must not be used as a
substitute for the biological measurement.

## Deferred reconciliation

The following work is intentionally deferred until the experiment owner
confirms the source records:

- determine why 41 L6000-defined compound wells have no image in the current
  snapshot;
- identify the 11 additional Plate 8 internal positions represented by the 185
  `unassigned` image records;
- reconcile the reported 591 compounds, 623 L6000 entries, and 582 mapped
  compound wells;
- confirm the hit threshold, normalization formula, replicate definitions,
  sample sizes, and candidate-comparison statistics;
- document Scellseg version, parameters, and image-exclusion rules;
- decide whether the nine incomplete whole-well channel pairs should be kept
  as partial observations or removed from the public image set; and
- reconcile the reported 4,886 isolated worms with the 4,878 instance TIFFs
  present in each of the `single-*` and `output-*` directory groups.

Recommended future public tables are `measurements.tsv` (one row per
single-worm observation), `compounds.tsv` (one row per plate/well assignment),
and a SHA-256 manifest for the 13,271 released images.
