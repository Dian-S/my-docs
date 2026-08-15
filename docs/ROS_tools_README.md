# Scellseg Single-Worm Image Processing

The packaged source, environment, configuration template, helper scripts, and
full command-level workflow are available in `../../scellseg_analysis/` and
[`ROS_scellseg_analysis_workflow.md`](ROS_scellseg_analysis_workflow.md).

This document describes how Scellseg relates to the *C. elegans* HyPer2
screening image dataset. It records the processing chain that can be verified
from the distributed files and separates it from settings that remain unknown.

## Tool role

[Scellseg](https://github.com/cellimnet/scellseg-publish) is a style-aware deep
learning tool for adaptive instance segmentation. Its official workflow
supports image annotation, pre-trained models, contrastive or conventional
fine-tuning, inference, batch segmentation, and export of individual instance
images.

In this project, Scellseg was used to identify individual worms in whole-well
fluorescence images and generate per-worm image crops for downstream ImageJ
measurement.

## Observed project workflow

```text
whole-well w1 TIFF
        ↓
query input copy (*_w1_img.tif)
        ↓
Scellseg instance segmentation
        ├── instance mask PNG
        ├── segmentation-preview PNG
        ├── segmentation array NPY
        └── outline TXT
        ↓
individual-worm TIFFs (16-bit, 512 × 512)
        ↓
8-bit TIFF conversion (512 × 512)
        ↓
ImageJ measurements (Area, Mean, Min, Max, IntDen, and RawIntDen)
```

This reconstruction is based on filenames, directory structure, image
properties, and the columns present in the measurement exports. No original
batch command, configuration file, model checkpoint, or processing log was
found in the supplied project snapshot.

## Input images

The Scellseg query directories contain 702 TIFF inputs:

| Property | Observed value |
|---|---|
| Channel | `w1`, FITC/GFP |
| Resolution | 2007 × 2007 pixels |
| Bit depth | 16-bit |
| Batches | Eight query directories |
| Filename suffix | `_w1_img.tif` |

The raw `w2` DAPI/Violet images do not appear in the Scellseg query, single,
or output directories. The verified processing files therefore document
segmentation of `w1` images only. They are insufficient by themselves to
reconstruct a paired `YFP500/YFP420` measurement.

A checked `query` TIFF was byte-identical to its corresponding raw `w1` TIFF,
which indicates that query images may be processing copies. A complete
checksum comparison is still required before all 702 query TIFFs can be
treated as duplicates during public packaging.

## Observed outputs

### Segmentation artifacts

Each of the 702 query images has the following associated files:

| Suffix | Files | Observed role | Image-release status |
|---|---:|---|---|
| `_cp_masks.png` | 702 | Instance-mask image, 2007 × 2007, 8-bit | Included as a processing image |
| `_cp_output.png` | 702 | Segmentation preview, 3600 × 900, 8-bit | Included as a processing image |
| `_seg.npy` | 702 | Segmentation array | Excluded from the image-only release |
| `_cp_outlines.txt` | 702 | Instance outlines | Excluded from the image-only release |

The `_cp_*` and `_seg.npy` naming follows the Cellpose/Scellseg-style output
convention visible in the source data.

### Individual-worm TIFFs

The eight `single-*` directories contain 4,878 individual-worm TIFFs:

| Property | Observed value |
|---|---|
| Resolution | 512 × 512 pixels |
| Bit depth | 16-bit |
| Channel label | FITC/GFP (`w1`) |
| Filename suffix | `_w1_img_<instance>.tif` |

The eight `output-*` directories contain the same number of instance-labelled
TIFFs at 512 × 512 pixels, but they are 8-bit rather than 16-bit. A sampled
`single`/`output` pair was not byte-identical, so these directories should not
be treated as duplicate copies solely because their filenames correspond.

Each `output-*` directory also contains a `Results.xls` file. These files are
tab-delimited text exports rather than binary Excel workbooks and contain
ImageJ-style fields including `Area`, `Mean`, `Min`, `Max`, `IntDen`,
`RawIntDen`, `MinThr`, and `MaxThr`. They are not part of the image-only public
release.

## Count reconciliation

| Processing image group | Images |
|---|---:|
| Query TIFF inputs | 702 |
| Mask and preview PNGs | 1,404 |
| `single-*` 16-bit individual-worm TIFFs | 4,878 |
| `output-*` 8-bit individual-worm TIFFs | 4,878 |
| **Total Scellseg-related TIFF and PNG files** | **11,862** |

The manually supplied description reports 4,886 isolated worms, whereas the
distributed `single-*` and `output-*` directories each contain 4,878 TIFFs.
The eight-instance difference remains unresolved and should not be corrected by
inference.

## Official reference installation

The upstream repository documents the following basic installation and GUI
launch sequence:

```bash
conda create --name scellseg_env python=3.7
conda activate scellseg_env
pip install scellseg --default-timeout=10000
python -m scellseg
```

The upstream authors report a reference environment using Python 3.7.4, CUDA
10.1.243, and an NVIDIA 2080 Ti, with testing on Windows 10 and Ubuntu 18.04.
These are upstream reference details, not a confirmed record of the environment
used for this dataset.

The official GUI documentation describes default inference values of 0.4 for
model-match threshold and 0.5 for cell-probability threshold. These defaults
must not be reported as project parameters unless confirmed by the experiment
owner or recovered configuration files.

## Parameters required for exact reproduction

The following project-specific information is currently missing:

- Scellseg package version or source commit;
- model type and checkpoint filename;
- whether the model was used as pre-trained or fine-tuned for worms;
- training images, masks, and shot/query split if fine-tuning was performed;
- selected segmentation channel and any second channel;
- cell diameter in pixels;
- model-match and cell-probability thresholds;
- batch size, device, GPU, CUDA, and PyTorch versions;
- manual mask corrections and instance-exclusion criteria;
- procedure that generated the 16-bit `single-*` crops;
- conversion and thresholding procedure for the 8-bit `output-*` TIFFs; and
- ImageJ version, macro, measurement settings, and QC rules.

Without these fields, the archived files document the output of the workflow
but do not yet support exact end-to-end rerunning.

## Recommended quality control

- Visually review masks and previews for merged worms, fragmented worms,
  debris, edge truncation, and empty instances.
- Preserve the relationship among the source well, query TIFF, mask, preview,
  and numbered instance TIFFs.
- Do not assume that the number of instance crops equals the biological sample
  size until exclusions and repeated outputs are reconciled.
- Retain 16-bit `single-*` images as the intensity-preserving derivative.
- Treat 8-bit `output-*` images as a separate processing stage and document the
  conversion before quantitative reuse.
- Do not infer a paired-channel ratio from `w1`-only instance files.
- Generate checksums before removing possible query copies or other redundant
  files from the public package.

## Software citation

If Scellseg-derived images are reused, cite both the software paper and the
dataset:

> Xun D, Chen D, Zhou Y, Lauschke VM, Wang R, Wang Y. Scellseg: a style-aware
> deep learning tool for adaptive cell instance segmentation by contrastive
> fine-tuning. *iScience*. 2022;25:105506.
> https://doi.org/10.1016/j.isci.2022.105506

Upstream source code and licence:

- https://github.com/cellimnet/scellseg-publish
- BSD 3-Clause licence, as reported by the upstream repository
