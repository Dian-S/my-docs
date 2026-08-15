# Data Structure

## Release scope

The release contains screening-related TIFF images, image-level metadata, and
compound/reference workbooks. Final presentation composites and later
validation or mechanism experiments are outside scope.

## Logical layout

```text
C_elegans_COL12_Collagen_Secretion_Dataset/
├── screening_images/
│   ├── plate_acquisitions/          # raw w1 and w2 whole-well TIFFs
│   └── single_worm_processing/      # 16-bit and 8-bit single-worm TIFFs
├── metadata/
│   └── metadata.xlsx
└── reference_tables/
    └── L6000-Natural_Compound_Library-to_Ni_Ai.xlsx 
```

The logical names above are recommended public-release names. The current
source tree retains acquisition-date, plate-group, complement, supplement,
`input`, `output`, and `single_missingoutput` directory names. Keep
`relative_path` unchanged until a migration manifest is generated.

## Image inventory

| Image class | Images | Resolution | Bit depth |
|---|---:|---|---|
| Raw whole-well TIFFs | 2,186 | 1,820 at 2007 × 2007; 366 at 4015 × 4015 | 16-bit |
| Single-worm crop TIFFs | 4,718 | 512 × 512 | 16-bit |
| Processed single-worm TIFFs | 7,027 | 512 × 512 | 8-bit |
| **Released TIFFs** | **13,931** | — | — |

## Raw acquisition pairing

A representative filename is:

```text
20220418-fjy-plate2_B09_sx_1_sy_1_w1.tif
```

The name identifies the acquisition, plate, well, field position, and channel:

- `w1`: FITC/GFP reporter fluorescence;
- `w2`: transmitted light.

The 2,186 raw files represent 1,099 acquisition positions:

| Channel availability | Positions | TIFF files |
|---|---:|---:|
| Complete `w1 + w2` pair | 1,087 | 2,174 |
| Only `w2` | 11 | 11 |
| Only `w1` | 1 | 1 |
| **Total** | **1,099** | **2,186** |

Repeated, supplemented, or re-imaged acquisitions mean that acquisition
positions must not be equated directly with the 614 reported compounds.

## Single-worm processing groups

| Source group | 16-bit TIFFs | 8-bit TIFFs | Relationship |
|---|---:|---:|---|
| Plate groups 1, 3, 7, and 8 | 1,286 | 1,286 | Exact filename pairs |
| Plate groups 2, 4, 5, and 6 | 3,432 | 3,432 | Exact filename pairs |
| Complement/re-array output | 0 | 2,122 | Parent/input relation unresolved |
| `single_missingoutput` | 0 | 184 | Directory role unresolved |
| Additional Plate 6 G11 results | 0 | 3 | Additional processing records |
| **Total** | **4,718** | **7,027** | — |

The 16-bit and 8-bit images are separate processing stages and should not be
deduplicated solely because 4,718 filenames correspond.

## Compound mapping

Original library compounds are joined using `plate_id + well_id` against the
supplied L6000 workbook. Control positions are preserved separately. The
complement/re-array acquisition label is not treated as an original L6000
plate; those wells remain unresolved unless independent candidate-list
evidence exists.

