# Data Structure

## Top-Level Layout

```text
Doxorubicin_Induced_Heart_Failure_Dataset/
└── dox/
    ├── 2020112718/
    │   ├── C-*.tiff
    │   ├── M-*.tiff
    │   └── DXZ-*.tiff
    ├── 2020121220/
    ├── ... additional date/date-time experiment batches ...
    ├── condition_optimization/
    ├── Tanshinone/
    │   ├── first_round/
    │   └── second_round/
    ├── Ganoderma/
    ├── zebrafish_display_images/      # source archive only; excluded
    └── SequenceTIF.txt                # source archive only; excluded
```

The tree above describes the source archive. The curated database preserves
the relative paths of included images but omits files covered by the exclusion
rules below.

Metadata downloads: [`metadata/metadata.xlsx`](metadata/DOX_metadata.xlsx) and
[`metadata/compound_plate_map.xlsx`](metadata/DOX_compound_plate_map.xlsx).

## Section Summary

| Section | Files | Approx. size | Description |
|---|---:|---:|---|
| `condition_optimization` | 329 | 59.07 GiB | Imaging and DIC-condition optimization |
| `Tanshinone` | 118 | 5.48 GiB | Named-compound imaging; derived analysis excluded |
| `Ganoderma` | 3 | 0.10 GiB | Named-compound imaging |
| Other date/date-time experiment batches | 2,879 | 157.48 GiB | Per-batch control, model, and treatment-group images |
| **Curated database total** | **3,329** | **222.12 GiB** | Included TIFF, TIF, and SIF imaging files |

## Organization Principle

The main organizational unit is the experiment batch:

1. A top-level date or date-time folder identifies one acquisition/experiment.
2. Files inside that folder represent the different groups included in that
   experiment.
3. Group identity is encoded mainly in the filename, including raw labels such
   as `C`, `Con`, model-group labels, positive-control labels, and other
   administered-treatment codes.
4. Numeric suffixes generally distinguish individual fish or replicates. For
   numbered screening compounds, `350-1` means compound-library number 350,
   fish/replicate 1. The compound identity is resolved through
   [`metadata/compound_plate_map.xlsx`](metadata/DOX_compound_plate_map.xlsx); in this example, compound 350 is
   cyanidin chloride.
5. Named-treatment files generally follow a treatment-dose-fish pattern.
   `M-30-1-1` means model group, 30 h modeling, fish 1, extra view 1; the
   corresponding `M-30-1` is the primary view.

Within the fixed metadata template, `relative_path` preserves the top-level
batch folder and `file_name` preserves the original group or treatment label.

## Largest Experiment Batches

| Folder | Files | Approx. size |
|---|---:|---:|
| `condition_optimization` | 329 | 59.07 GiB |
| `2021041016` | 172 | 11.15 GiB |
| `2021031316` | 105 | 10.21 GiB |
| `2021013018` | 104 | 10.11 GiB |
| `2021040414` | 148 | 9.59 GiB |
| `2021030612` | 98 | 9.53 GiB |
| `2021020215` | 87 | 8.46 GiB |
| `2021041114` | 126 | 8.17 GiB |
| `2021032010` | 103 | 6.67 GiB |
| `2021022711` | 64 | 6.22 GiB |
| `Tanshinone` | 118 | 5.48 GiB |

## File-Type Summary

| File type | Files | Approx. size | Description |
|---|---:|---:|---|
| `.tiff` | 3,190 | 186.23 GiB | Primary multi-frame heartbeat image stacks |
| `.sif` | 91 | 34.32 GiB | Andor acquisition files |
| `.tif` | 48 | 1.57 GiB | Image stacks retained in the curated database |

## File Naming Notes

Current folder and file names encode useful experiment information but are not
fully standardized. Examples include:

- Experiment dates: commonly encoded as `YYYYMMDD`, date-time-like, or other
  date-prefixed folder names
- Group labels: `C` and `Con` are control labels; `M` denotes the model group;
  `DXZ` and `YANG` denote dexrazoxane. Original labels remain unchanged in
  filenames.
- Time notation: `XI` denotes hours.
- Drug or treatment labels: `VIS` = visnagin; `TET` = tetrandrine; `CZS` =
  herbacetin; `DANC` = tanshinone; `lhscjs`, `lv`, and `LV` = cyanidin chloride;
  `IA` = isochlorogenic acid; `ISO` = isoproterenol; `Cha A` = neohesperidin
  dihydrochalcone; `LV+RSL` = cyanidin chloride plus RSL3; `3-MA` = autophagy
  inhibitor; `DAN-B` = salvianolic acid B; `GXN` = Guanxinning; `sx` =
  Danshen-Chuanxiong formula; `becs` = epicatechin; `hjtg` = salidroside;
  `hupisu` = quercetin; `lxfg` = astilbin; `MDXS` = rosmarinic acid; `MGG` =
  mangiferin; `SFJB` = silibinin; and `yoqhs` = isoimperatorin.
- Replicate numbers: commonly encoded with numeric suffixes
- Experiment type: semantic labels include `condition_optimization`, `ros`,
  `ISO`, `Tanshinone`, and `yizhiji` (inhibitor)

The image metadata workbook preserves original relative paths and filenames.
The separate compound plate map provides English compound names, retained
Chinese source names, CAS numbers, and mapping status. The codebook above
documents confirmed interpretations without rewriting the raw labels.

## Curation Exclusions

The curated database excludes 98 source-archive files:

- 31 display images, including paths or names containing
  `zebrafish_display_images`, `zanshi`, or `zhanshi`;
- 27 statistical or derived outputs, including `data_processing`,
  `statistical_analysis`, EDA, ESA, FAC, FS, SV, and heart-rate outputs;
- 2 dead-specimen files marked `SILE` or `-SI`;
- 5 unresolved files beginning with `Z-`;
- 32 unresolved files beginning with `mei-`;
- 1 non-image support file.

Files marked `jixing` are retained as deformed/abnormal phenotypes, files
marked `XUELIU` are retained as blood-flow images, and `dxz-n` is treated as an
ordinary DXZ replicate.
