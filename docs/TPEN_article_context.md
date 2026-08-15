# Article Context and Dataset Mapping

## Associated article

Chen J, Ren C, Yao C, Baruscotti M, Wang Y, Zhao L. Identification of the natural chalcone glycoside hydroxysafflor yellow A as a suppressor of P53 overactivation-associated hematopoietic defects. *MedComm*. 2023;4:e352. https://doi.org/10.1002/mco2.352

## Study purpose

The study investigated hematopoietic defects associated with zinc deficiency and P53 overactivation. The authors established a TPEN-induced zebrafish model and used fluorescence-labeled HSCs as an in vivo phenotypic-screening readout to identify hematopoietic-protective natural compounds.

## Zebrafish screening model

- Species: zebrafish (*Danio rerio*)
- Reporter line: `Tg(runx1:eGFP)`
- Biological readout: number of fluorescent HSC signals in the caudal hematopoietic tissue (CHT)
- Model induction: 150 uM TPEN at 2.5 dpf
- Screening compounds: 100 uM, added simultaneously with TPEN
- Positive rescue control: 100 uM ZnSO4
- Vehicle control: 0.1% DMSO
- Replication: 5–8 embryos per group
- Imaging time: 12 h after treatment
- Microscope: Leica DMI 3000B inverted microscope system
- Quantification: ImageJ 1.53c, `Convolve`, then `Find Maxima` with noise tolerance 30 and count
- Animal ethics approval reported by the article: ZJU20230216

## Screening design from the article

- Compound library: 102 natural molecules associated with hematopoietic or blood-related functions
- Screening metric: HSC count in the CHT
- Efficacy score: `(N_drug - N_model) / (N_control - N_model)`
- Positive threshold: efficacy score greater than 0.85
- Safety filter: treatments producing a mean HSC count above the normal-control level were excluded from hit selection
- Main selected hit: hydroxysafflor yellow A (HSYA)
- Follow-up screening result: HSYA rescue was validated in a dose-dependent manner in zebrafish

## Main findings relevant to this dataset

- TPEN reduced `runx1:eGFP`-positive HSC signals in the zebrafish CHT.
- Zinc supplementation rescued the TPEN-associated hematopoietic phenotype and served as the positive rescue control.
- Ten supplied compound-reference scores exceed 0.85; three exceed 1 and are marked as above-normal exclusions in the documentation reference table.
- HSYA has a supplied efficacy score of approximately 0.952 and was selected for further validation in the article.

The article also contains mechanistic, cell-based, and mouse experiments. Those experiments are not represented in the current public image dataset or image-level metadata.

## Mapping dataset folders to screening content

| Dataset folder | Image files | Article-related content | Notes |
|---|---:|---|---|
| `3-4` | 308 | Screening compounds, controls, TPEN model, and zinc rescue images | Contains SIF source files and TIFF representations |
| `3.13_screening` | 353 | Primary-screening compound and control groups | Treatment identity is encoded mainly by compound number or name |
| `3.19_screening` | 311 | Primary-screening compound and control groups | Contains the matched Control, TPEN, and HSYA demonstration batch used in the workflow documentation |
| `4.6` | 247 | Primary-screening compound and control groups | Filename conventions vary by treatment and replicate |

The four sections contain 1,219 image files in total. Exact image-level paths and technical attributes are recorded in [`metadata/metadata.xlsx`](metadata/TPEN_metadata.xlsx); treatment-label interpretation is provided in [`metadata/TPEN_compound_reference.xlsx`](metadata/TPEN_compound_reference.xlsx).

## Dataset-to-article boundary

The dataset is an article-linked screening-image collection, not a complete archive of every experiment reported in the publication. Inclusion in the dataset means that an image belongs to the curated zebrafish screening scope; it does not imply that every file was displayed directly in the published article.
