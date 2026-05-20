# Data Structure

## Top-Level Layout

```text
ZF_APOC2/
├── 模型/
│   ├── bodipy/
│   ├── 光镜/
│   └── 油红O/
└── 筛药/
    ├── 2023-11-10-tif/
    ├── 20231029-tif/
    ├── 20231119-tif/
    ├── 20231202-tif/
    ├── tif/
    └── tif-1/
```

## Section Summary

| Section | Files | Approx. size | Description |
|---|---:|---:|---|
| `模型/bodipy` | 269 | 114 MB | BODIPY staining images for model-related experiments |
| `模型/光镜` | 189 | 44 MB | Brightfield images, including swim bladder phenotype comparison |
| `模型/油红O` | 304 | 44 MB | Oil Red O staining images |
| `筛药` | 1,116 | 667 MB | Drug screening TIFF images |

## Model Section Detail

### `模型/bodipy`

| Folder | Files | Approx. size |
|---|---:|---:|
| `20220302(6dpf)D3921Bodipy染色` | 22 | 7.5 MB |
| `20220921 3dpf bodipy` | 28 | 9.5 MB |
| `20220922 4dpf bodipy` | 32 | 11 MB |
| `20220924 6dpf bodipy` | 37 | 13 MB |
| `20230614-apoc2质粒带荧光24hpf` | 11 | 6.6 MB |
| `20230618-apoc2质粒过表达5dpf` | 26 | 8.8 MB |
| `20230818-5dpf-positivedrug` | 37 | 22 MB |
| `20231023-5dpf-GEMF` | 41 | 25 MB |
| `bodipy` | 35 | 12 MB |

### `模型/光镜`

```text
模型/光镜/
└── Apoc2 纯合子鱼鳔出现时间对比/
    ├── 4dpf/
    ├── 4.5dpf/
    ├── 5dpf/
    ├── 5.5dpf/
    ├── 6dpf/
    └── 过表达挽救情况/
```

This section contains 189 JPEG images. Folder names indicate developmental-stage
comparisons and rescue-condition images.

### `模型/油红O`

| Folder | Files | Approx. size |
|---|---:|---:|
| `2021-11-23 6dpf` | 16 | 3.0 MB |
| `2021-12-24 6dpf` | 35 | 4.0 MB |
| `2022-01-12 6dpf` | 28 | 6.0 MB |
| `20220924 5dpf` | 30 | 5.0 MB |
| `20231203-5dpf` | 50 | 7.3 MB |
| `20231230-6dpf` | 56 | 8.0 MB |
| `20240116-6dpf` | 48 | 5.7 MB |
| `20240124-6dpf` | 41 | 5.4 MB |

## Drug Screening Section Detail

| Folder | Files | Approx. size |
|---|---:|---:|
| `筛药/2023-11-10-tif` | 153 | 91 MB |
| `筛药/20231029-tif` | 244 | 146 MB |
| `筛药/20231119-tif` | 199 | 119 MB |
| `筛药/20231202-tif` | 124 | 74 MB |
| `筛药/tif` | 284 | 170 MB |
| `筛药/tif-1` | 112 | 67 MB |

## File Naming Notes

Current filenames encode useful experiment information but are not fully
standardized. Examples include:

- Genotype or group labels: `AB`, `APOC2`, `apoc2`, `ctrl`, `apoc2mutant`
- Drug or treatment labels: examples include Chinese compound names and doses
- Replicate numbers: commonly encoded after a hyphen, such as `-1`, `-2`, `-3`
- Developmental stage: often encoded in folder names, such as `3dpf`, `5dpf`,
  or `6dpf`