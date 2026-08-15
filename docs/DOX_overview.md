# Doxorubicin-Induced Heart Failure Dataset Overview

The Doxorubicin-Induced Heart Failure Dataset is a zebrafish cardiac imaging
dataset associated with the article [Use of Deep-Learning Assisted Assessment of
Cardiac Parameters in Zebrafish to Discover Cyanidin Chloride as a Novel Keap1
Inhibitor Against Doxorubicin-Induced
Cardiotoxicity](https://doi.org/10.1002/advs.202301136), published in *Advanced
Science*.

The collection contains fluorescence heartbeat recordings from
`Tg(cmlc2:eGFP)` zebrafish used for DIC model development, cardiac-function
assessment, experimental-condition optimization, natural-compound screening,
and follow-up experiments. The source archive contains 3,427 files, while the
curated database contains 3,329 imaging files after applying the documented
exclusion rules. The database is intended to support zebrafish cardiac
phenotyping, image-based drug-response analysis, and reproducible curation of
article-linked imaging data.

**The current server location is internal and is not yet a confirmed public
download endpoint.**

## Available datasets

The current collection retains its original time-based experiment organization.
Most top-level folders identify one acquisition or experimental batch by date
or date-time. Files inside each batch represent the different groups examined
in that experiment, using raw filename labels such as `C`, `Con`, and codes for
the model or administered-treatment groups.

- date/date-time batch folders: cardiac imaging experiments conducted mainly
  from 2020 to 2023, with control and treatment groups stored together within
  each corresponding experiment batch;
- `condition_optimization`: DIC exposure, imaging, plate, and acquisition
  optimization experiments;
- `Tanshinone`: named-compound imaging experiments; derived analysis files are
  excluded from the curated database;
- `Ganoderma`: named-compound imaging experiments.

The source archive also contains selected display images and a small number of
statistical, derived, and support files. These are not part of the curated
database.

Current dataset summary:

| Dataset section | Files | Approx. size | Main content |
|---|---:|---:|---|
| `condition_optimization` | 329 | 59.07 GiB | Imaging and DIC-condition optimization |
| `Tanshinone` | 118 | 5.48 GiB | Named-compound imaging |
| `Ganoderma` | 3 | 0.10 GiB | Named-compound imaging |
| Other date/date-time experiment batches | 2,879 | 157.48 GiB | Per-experiment control, model, and treatment groups from DIC, screening, validation, inhibitor, ROS, and follow-up studies |
| **Curated database total** | **3,329** | **222.12 GiB** | TIFF, TIF, and SIF imaging files represented in [`metadata/metadata.xlsx`](metadata/DOX_metadata.xlsx) |

The 98 excluded source-archive files comprise 31 display images, 27
statistical or derived outputs, 2 dead-specimen files, 5 unresolved `Z` files,
32 unresolved `mei` files, and 1 non-image support file.

The dated folders should not be interpreted as separate dataset types. Each is
an experiment-level container, while group identity is encoded mainly in the
filenames within that folder. The original folder and filename structure should
be preserved in the public release.

A complete folder-level summary is available in [Data Structure](DOX_data_structure.md).

## Downloading the dataset

See [Data Structure](DOX_data_structure.md) for a description of the current data
organization.

Internal access and draft future-public-download instructions are provided in
[Download and Usage Instructions](DOX_download_usage.md).

## Experimental protocol versions

The dataset is linked to the 2023 *Advanced Science* article by Liu and
colleagues.

Key experimental context:

- Cardiac reporter line: `Tg(cmlc2:eGFP)`.
- DIC induction: 65 uM doxorubicin plus 10 uM FeCl3.
- DIC treatment window: 30 to 60 hpf.
- Imaging time: 100 hpf.
- Imaging restraint: 300 uM tricaine.
- Acquisition: 2 s per larva at 50 frames/s.
- Microscope: Leica DMI 3000B inverted microscope.
- Primary screening library: 347 medicinal-herb-derived natural compounds.
- Primary screening concentration: 100 uM.
- Replication: at least five larvae per compound.
- Main validated hit: cyanidin chloride (CyCl).
- Proposed mechanism: competitive binding to Keap1 and enhancement of
  Nrf2/Gpx4 signaling.

More article-specific context is summarized in [Article Context and Dataset
Mapping](DOX_article_context.md).

## Contributing to the dataset

The workbook [`metadata/metadata.xlsx`](metadata/DOX_metadata.xlsx) is the file manifest for the curated
database and contains one row per included imaging file. Original relative
paths and filenames are retained, while confirmed naming conventions and
treatment-code interpretations are documented without adding unverified
experimental-purpose assignments.

The companion workbook [`metadata/compound_plate_map.xlsx`](metadata/DOX_compound_plate_map.xlsx) maps numbered
screening compounds to English names, retained Chinese source names, CAS
numbers, and mapping status. It is used together with numbered filenames such
as `350-1.tiff`.

See [Metadata](DOX_metadata_plan.md) for the current fields, curation rules, and
remaining technical-metadata work.

## Analysis tool

The accompanying `dox_cardiac_analysis/` package organizes the supplied
ZVSegNet ventricular-segmentation model and HRNet heart-rate model into a
configuration-driven inference workflow. It accepts heartbeat TIFF/TIF stacks
or extracted frames and produces ventricular masks, ventricular-area
sequences, EDA, ESA, FAC, FS, SV, and heart-rate outputs. Because both
checkpoints were trained specifically for this project, they are bundled in
the tool's `models/` directory.

## Complementary datasets

For related public bioimage and phenotypic-screening resources, users may also
explore:

- [Cell Painting Gallery](https://broadinstitute.github.io/cellpainting-gallery/overview.html)
- [Image Data Resource](https://idr.openmicroscopy.org)

## Acknowledgments

The associated article reports support from the National Natural Science
Foundation of China (82173941, 31971088, and 62022072), the Zhejiang Provincial
Natural Science Foundation of China (LR23H280001 and LDT23H19012H19), the
Fundamental Research Funds for the Central Universities (226-2023-00114), and
the Innovation Team and Talents Cultivation Program of the National
Administration of Traditional Chinese Medicine (ZYYCXTD-D-202002).

The article acknowledges support from the ZJU PII-Molecular Devices Joint
Laboratory. Animal experiments were reported as approved by the Institutional
Animal Care and Use Committee of Zhejiang University under approval number
ZJU20230044.
