# TPEN Zebrafish Drug-Screening Dataset Overview

The TPEN Zebrafish Drug-Screening Dataset is an article-linked fluorescence microscopy dataset associated with [Identification of the natural chalcone glycoside hydroxysafflor yellow A as a suppressor of P53 overactivation-associated hematopoietic defects](https://doi.org/10.1002/mco2.352), published in *MedComm* in 2023.

The dataset contains primary phenotypic drug-screening images from the study. Tg(runx1:eGFP) zebrafish embryos were used to identify treatments that rescued hematopoietic stem cell (HSC) loss caused by the zinc chelator TPEN. The current public-data scope is restricted to 1,219 fluorescence microscopy images. Excel workbooks, GraphPad Prism projects, temporary files, and other processing or statistical files are not included.

## Available dataset

The current collection is organized into four screening batches.

| Dataset section | Image files | Approx. size | Main content |
|---|---:|---:|---|
| `3-4` | 308 | 211.48 MB | Named compounds, controls, zinc rescue, and TPEN model images |
| `3.13_screening` | 353 | 494.95 MB | Primary-screening groups identified mainly by compound number or treatment name |
| `3.19_screening` | 311 | 259.33 MB | Primary-screening groups identified mainly by compound number or treatment name |
| `4.6` | 247 | 210.21 MB | Primary-screening groups identified mainly by compound number or control label |
| **Total** | **1,219** | **1,175.96 MB** | Zebrafish drug-screening images |

A folder-level description is available in [Data Structure](TPEN_data_structure.md). Image-level fields are described in [Metadata](TPEN_metadata_plan.md).

The article-derived ImageJ quantification, reproducible outputs, example images, and screening summaries are described in [HSC-Counting Workflow](TPEN_hsc_counting_workflow.md). The accompanying Fiji macro and Python utilities are available in `tools/tpen_hsc_counting/`.

## Experimental context

The dataset corresponds to the primary zebrafish phenotypic screen reported by Chen et al. Key conditions from the article are:

- Biological model: Tg(runx1:eGFP) zebrafish embryos with fluorescently labeled HSCs.
- Model induction: 150 uM TPEN added at 2.5 days post fertilization.
- Screening treatment: natural compounds at 100 uM, added together with TPEN.
- Positive rescue control: ZnSO4 at 100 uM.
- Vehicle control: 0.1% DMSO.
- Group size: 5–8 embryos per treatment group.
- Imaging time: 12 h after treatment.
- Microscope: Leica DMI 3000B inverted microscope system.
- Primary readout: number of runx1:eGFP-positive HSC signals in the caudal hematopoietic tissue (CHT) region.

The article reports an enriched library of 102 natural molecules. Hydroxysafflor yellow A (HSYA) was selected as the main validated hit.

## Reported screening score

The screening efficacy score was defined as:

```text
efficacy score = (N_drug - N_model) / (N_control - N_model)
```

where `N_drug` is the HSC count in the drug-treated group, `N_model` is the count in the TPEN model group, and `N_control` is the count in the control group. Compounds with a score greater than 0.85 were considered to have a positive hematopoietic effect. Treatments that increased the HSC count above the normal-control level were excluded from hit selection because of the potential risk of excessive hematopoietic stimulation.

## Image formats

The dataset contains:

| Format | Files | Typical role |
|---|---:|---|
| `sif` | 575 | Andor source microscopy images |
| `tif` | 490 | TIFF image exports |
| `tiff` | 154 | TIFF image exports |

All 1,219 records are grayscale zebrafish fluorescence images annotated as FITC-channel images. The metadata records 920 images at 640 × 540 pixels and 299 images at 853 × 720 pixels.

## Metadata resources

- `metadata/metadata.xlsx`: one row per image, using English metadata values and dataset-relative paths.
- `metadata/TPEN_compound_reference.xlsx`: compound-number lookup and screening filename legend. English treatment names are primary; Chinese names are retained only as supplementary cross-references where useful.

The absence of a numeric compound identifier is not treated as an error when the treatment is identifiable by name. Examples include Ginsenoside Rb1, Senkyunolide I, Rosmarinic acid, Guanxinning, and the zinc rescue control.
