# Article Context and Dataset Mapping

## Associated Article

Liu C, Wang Y, Zeng Y, Kang Z, Zhao H, Qi K, Wu H, Zhao L, Wang Y. Use of
Deep-Learning Assisted Assessment of Cardiac Parameters in Zebrafish to Discover
Cyanidin Chloride as a Novel Keap1 Inhibitor Against Doxorubicin-Induced
Cardiotoxicity. *Advanced Science*. 2023;10:2301136.
https://doi.org/10.1002/advs.202301136

## Study Purpose

The study sought to establish a scalable zebrafish cardiac-phenotyping platform
for doxorubicin-induced cardiotoxicity and to use that platform to identify
cardioprotective compounds. Fluorescent heartbeat recordings were combined with
deep-learning-assisted ventricular segmentation and heart-rate estimation to
quantify cardiac dysfunction and compound response.

## Experimental Model

- Species: zebrafish (*Danio rerio*)
- Cardiac reporter: `Tg(cmlc2:eGFP)`
- Disease model: doxorubicin-induced cardiomyopathy (DIC)
- DIC induction: 65 uM doxorubicin plus 10 uM FeCl3
- Treatment window: 30 to 60 hpf
- Imaging time: 100 hpf
- Imaging restraint: 300 uM tricaine
- Acquisition: 2 s at 50 frames/s
- Imaging system: Leica DMI 3000B inverted microscope
- Positive/reference treatment: dexrazoxane (DXZ), 450 uM
- Animal ethics approval: ZJU20230044

## Screening Design From the Article

- Compound library: 347 medicinal-herb-derived natural compounds
- Primary screening concentration: 100 uM
- Treatment window for screening compounds: 30 to 100 hpf
- Replication: at least five larvae per compound
- Quantitative readouts: EDA, ESA, FAC, FS, SV, and HR
- Additional readout: normal versus pericardial-edema phenotype
- Primary-screen result: 38 compounds with efficacy score above 0.7
- Main followed-up hit: cyanidin chloride (CyCl)

## Main Findings Relevant to the Dataset

- The zebrafish DIC model showed impaired systolic function, reduced heart rate,
  ventricular-shape changes, pericardial edema, and reduced peripheral blood flow.
- The article reports 2,125 manually labeled ventricular frames, augmented to
  5,100 images for ventricular segmentation.
- The article reports 296 heartbeat videos, each represented by 100 frames and
  containing at least four cardiac cycles, for heart-rate modeling.
- CyCl improved zebrafish cardiac parameters and reduced Dox-associated injury.
- Mechanistic experiments supported Keap1 binding and Nrf2/Gpx4-dependent
  protection against lipid peroxidation and ferroptosis.
- Protective effects were further evaluated in cardiomyocytes and acute/chronic
  mouse DIC models.

## Mapping Dataset Folders to Article Content

| Dataset folder | Likely article-related content | Notes |
|---|---|---|
| date/date-time imaging batches from 2020 to 2023 | Experiment-level DIC model development, cardiac recordings, screening, or follow-up work; each batch contains its control and treatment groups | Individual-file experimental purpose is not inferred in metadata |
| `condition_optimization` | Imaging, plate, exposure, and acquisition-condition development | Imaging files are included in the curated database |
| `Tanshinone` | Named-compound imaging | Statistical and derived measurement files are excluded from the curated database |
| `Ganoderma` | Named-compound imaging | Relationship to the article requires confirmation |
| `20211207-ros` | ROS-related imaging | Possibly mechanistic or follow-up work |
| folders ending in `yizhiji` | Inhibitor experiments | May correspond to regulated-cell-death inhibitor comparisons |
| `2023-3-18-ISO` and `2023-3-24-ISO` | Isoproterenol heart-failure experiments | Likely generalizability or later repeat/follow-up experiments |
| `zebrafish_display_images` | Selected display images in the source archive | Excluded from the curated database and planned public release |

Folder names provide batch context, but the metadata does not infer an
experimental purpose for individual files. Confirmed filename interpretations
and the curation exclusions are documented in [Data Structure](DOX_data_structure.md).
