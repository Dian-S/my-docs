# Data Structure

## Top-Level Layout

```text
ZF_APOC2/
├── model/
│   ├── bodipy/
│   ├── brightfield/
│   └── oil_red_o/
└── drug_screen/
    ├── 2023_11_10_tif/
    ├── 20231029_tif/
    ├── 20231119_tif/
    ├── 20231202_tif/
    ├── tif/
    └── tif_1/
```

## Section Summary

| Section | Files | Approx. size | Description |
|---|---:|---:|---|
| `model/bodipy` | 269 | 114 MB | BODIPY staining images for model-related experiments |
| `model/brightfield` | 189 | 44 MB | Brightfield images, including swim bladder phenotype comparison |
| `model/oil_red_o` | 304 | 44 MB | Oil Red O staining images |
| `drug_screen` | 1,116 | 667 MB | Drug screening TIFF images |

## Model Section Detail

### `model/bodipy`

| Folder | Files | Approx. size |
|---|---:|---:|
| `20220302_6dpf_D3921_BODIPY_staining` | 22 | 7.5 MB |
| `20220921_3dpf_bodipy` | 28 | 9.5 MB |
| `20220922_4dpf_bodipy` | 32 | 11 MB |
| `20220924_6dpf_bodipy` | 37 | 13 MB |
| `20230614_apoc2_plasmid_fluorescence_24hpf` | 11 | 6.6 MB |
| `20230618_apoc2_plasmid_overexpression_5dpf` | 26 | 8.8 MB |
| `20230818_5dpf_positive_drug` | 37 | 22 MB |
| `20231023_5dpf_GEMF` | 41 | 25 MB |
| `bodipy` | 35 | 12 MB |

### `model/brightfield`

```text
model/brightfield/
└── apoc2_homozygote_swim_bladder_formation_timing/
    ├── 4dpf/
    ├── 4.5dpf/
    ├── 5dpf/
    ├── 5.5dpf/
    ├── 6dpf/
    └── overexpression_rescue/
```

This section contains 189 JPEG images. Folder names indicate developmental-stage
comparisons and rescue-condition images.

### `model/oil_red_o`

| Folder | Files | Approx. size |
|---|---:|---:|
| `2021_11_23_6dpf` | 16 | 3.0 MB |
| `2021_12_24_6dpf` | 35 | 4.0 MB |
| `2022_01_12_6dpf` | 28 | 6.0 MB |
| `20220924_5dpf` | 30 | 5.0 MB |
| `20231203_5dpf` | 50 | 7.3 MB |
| `20231230_6dpf` | 56 | 8.0 MB |
| `20240116_6dpf` | 48 | 5.7 MB |
| `20240124_6dpf` | 41 | 5.4 MB |

## Drug Screening Section Detail

| Folder | Files | Approx. size |
|---|---:|---:|
| `drug_screen/2023_11_10_tif` | 153 | 91 MB |
| `drug_screen/20231029_tif` | 244 | 146 MB |
| `drug_screen/20231119_tif` | 199 | 119 MB |
| `drug_screen/20231202_tif` | 124 | 74 MB |
| `drug_screen/tif` | 284 | 170 MB |
| `drug_screen/tif_1` | 112 | 67 MB |

## File Naming Notes

Current filenames encode useful experiment information but are not fully
standardized. Examples include:

- Genotype or group labels: `AB`, `APOC2`, `apoc2`, `ctrl`, `apoc2mutant`
- Drug or treatment labels: examples include English compound names or plate codes with doses
- Replicate numbers: commonly encoded after a hyphen, such as `-1`, `-2`, `-3`
- Developmental stage: often encoded in folder names, such as `3dpf`, `5dpf`,
  or `6dpf`
