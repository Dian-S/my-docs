# Data Structure

## Release scope

This release is an image dataset. It contains screening-related TIFF and PNG
files together with an image-level metadata workbook and a plate-to-compound
reference table.


## Logical layout

```text
C_elegans_ROS_Dataset/
├── screening_images/
│   ├── plate_acquisitions/          # raw paired-channel TIFF images
│   └── single_worm_processing/      # derived TIFF and PNG images
├── metadata/
│   └── metadata.xlsx
└── reference_tables/
    └── L6000-Natural_Compound_Library-to_Ni_Ai.xlsx
```

## Image inventory

| Image class | TIFF | PNG | Total |
|---|---:|---:|---:|
| Raw plate/well acquisitions | 1,409 | 0 | 1,409 |
| Single-worm and image-processing outputs | 10,458 | 1,404 | 11,862 |
| **Total** | **11,867** | **1,404** | **13,271** |

## Whole-well acquisitions

A representative filename is:

```text
20220707-FJY-PLATE6-SINGLE_D03_sx_1_sy_1_w2.tif
```

The filename encodes acquisition date, plate, well, field position, and
channel:

- `w1`: FITC/GFP channel, approximately 488 nm excitation and 525 nm emission;
- `w2`: DAPI/Violet channel, approximately 405 nm excitation.

The 1,409 TIFF files represent 709 unique plate/well positions rather than
1,409 wells. Pairing status is:

| Channel availability | Plate/well positions | TIFF files |
|---|---:|---:|
| Complete `w1 + w2` pair | 700 | 1,400 |
| Only one expected channel present | 9 | 9 |
| **Total** | **709** | **1,409** |

Of the nine incomplete pairs, seven contain only `w2` and two contain only
`w1`. They are retained in the source inventory but may be excluded from any
analysis that requires the `YFP500/YFP420` paired-channel measurement.

## Single-worm and processing outputs

These TIFF and PNG files are derivatives generated during segmentation and
image processing. 

See the [Scellseg Analysis Workflow](ROS_scellseg_analysis_workflow.md) for the
observed query, mask, preview, 16-bit single-worm, and 8-bit output stages and
for the accompanying source-code package.

The documentation deliverable also contains `scellseg_analysis/` and
`scellseg_analysis.zip`. These package source code, environment definitions,
configuration placeholders, and helper scripts; project model weights are
currently marked as missing.

## Compound mapping

Compound identity is joined from the supplied L6000 workbook using
`plate_id + well_id`. Experimental columns 1 and 12 are controls.
