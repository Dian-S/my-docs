# ZF_APOC2 Overview

The ZF_APOC2 dataset is a publicly shareable zebrafish microscopy image dataset associated with the article [High-throughput screening reveals paeoniflorin's efficacy against Apoc2-deficient hypertriglyceridemia via HNF4A/PPARA/LDLR](https://doi.org/10.1016/j.bcp.2025.117351), published in *Biochemical Pharmacology*.

The dataset contains images from an `apoc2`-deficient zebrafish hypertriglyceridemia model and natural small-molecule phenotypic screening. The image collection includes BODIPY staining, Oil Red O staining, brightfield images, and drug-screening images. The current dataset package contains 1,878 image files and is intended to support zebrafish disease model characterization, lipid phenotype analysis, and image-based drug-response analysis.

**Access does not require an AWS account** .

## Available datasets

The current ZF_APOC2 collection is organized into two top-level sections:

- `模型`: images related to Apoc2 model construction, phenotype validation, staining experiments, and rescue/positive-control experiments.
- `筛药`: TIFF images related to drug-screening experiments.

Current dataset summary:

| Dataset section | Files | Approx. size | Main content |
|---|---:|---:|---|
| `模型/bodipy` | 269 | 114 MB | BODIPY staining images |
| `模型/光镜` | 189 | 44 MB | Brightfield phenotype images |
| `模型/油红O` | 304 | 44 MB | Oil Red O staining images |
| `筛药` | 1,116 | 667 MB | Drug-screening TIFF images |

A complete folder-level summary is available in [Data Structure](data_structure.md).

## Downloading from ZF_APOC2

See [Data Structure](data_structure.md) for a description of data organization in the ZF_APOC2 dataset.

Detailed instructions for browsing and downloading the dataset will be provided in [Download and Usage Instructions](download_usage.md).
## Experimental protocol versions

The dataset corresponds to the 2025 *Biochemical Pharmacology* article by Li, Qi, Wu, Shen, and Zhao.

Key experimental context:

- Disease model: CRISPR/Cas9-generated `apoc2` knockout zebrafish.
- Primary screening library: 351 natural small molecules.
- Primary screening concentration: 100 uM.
- Treatment window: 48 hpf to 6 dpf.
- Image readout: BODIPY 505/515 fluorescence signal in the caudal vessel.
- Positive control: gemfibrozil (GEMF), 2.5 uM.
- Main validated hit: paeoniflorin (PAE).
- Proposed mechanism: HNF4A/PPARA/LDLR signaling, triglyceride-rich lipoprotein clearance, beta-oxidation, and lipophagy.

More article-specific context is summarized in [Article Context and Dataset Mapping](article_context.md).

## Contributing to ZF_APOC2

Before public release, the existing `metadata/metadata.xlsx` workbook should be expanded with experiment-level fields. It already contains one row per image and can serve as the public image inventory.

Suggested public metadata:

- `metadata/metadata.xlsx`: one row per image in the `images` sheet.
- optional experiment-level sheet: one row per experiment folder or batch.

Recommended metadata fields include relative file path, assay type, experiment date, developmental stage, genotype/model group, treatment, dose, replicate number, and the corresponding article experiment or figure panel when available.

See [Metadata](metadata_plan.md) for the current fields and recommended additions.

## Complementary datasets

For related public bioimage and phenotypic-screening resources, users may also explore:

- [Cell Painting Gallery](https://broadinstitute.github.io/cellpainting-gallery/overview.html)
- [Image Data Resource](https://idr.openmicroscopy.org)

## Acknowledgments

The associated article reports support from the National Key R&D Program of China (Grant No. 2024YFC3506601) and the Zhejiang Provincial Natural Science Foundation of China (Grant No. LR23H280001).

The article acknowledges ZJU PII-Molecular Devices Laboratory and technical contributions from Yingniang Li and Jingyao Chen at Zhejiang University School of Medicine Core Facilities.

Zebrafish experiments were conducted under the guidelines of the Animal Ethics Committee of the Laboratory Animal Center, Zhejiang University, approval number ZJU20250466.
