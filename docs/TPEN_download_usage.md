# Download and Usage Instructions

This page describes the intended public-access layout for the TPEN zebrafish drug-screening image dataset. Repository and bucket identifiers remain placeholders until the public deposit is created.

## Dataset root

Current internal source location:

```text
/data/volume3/share_storage/dian/Dataset/TPEN_Induced_Hematopoietic_Defects_Dataset_HSCs/
```

The public image release should preserve the screening-batch structure documented in [Data Structure](TPEN_data_structure.md):

```text
TPEN_Drug_Screening_Dataset/
├── 3-4/
├── 3.13_screening/
├── 3.19_screening/
└── 4.6/
```

The release scope contains 1,219 fluorescence microscopy images. Excel analysis workbooks, GraphPad Prism projects, temporary files, mouse experiments, cell-culture assays, and western blots are excluded.

## Documentation download

The documentation archive contains:

```text
TPEN_Drug_Screening_Dataset_docs/
├── README.md
├── PACKAGE_CONTENTS.md
├── docs/
└── metadata/
    ├── metadata.xlsx
    └── TPEN_compound_reference.xlsx
```

The Fiji/ImageJ macro and Python utilities are distributed separately as `TPEN_HSC_Counting_Toolkit.zip`.

## Planned public-object-storage access

Replace the placeholders below after repository deposition.

S3 URI:

```text
s3://<bucket-name>/<optional-prefix>/
```

Download with the AWS CLI:

```bash
aws s3 sync --no-sign-request \
  s3://<bucket-name>/<optional-prefix>/ \
  ./TPEN_Drug_Screening_Dataset/
```

List files without downloading:

```bash
aws s3 ls --no-sign-request --recursive \
  s3://<bucket-name>/<optional-prefix>/
```

## File usage

- Use [`metadata/metadata.xlsx`](metadata/TPEN_metadata.xlsx) as the image inventory and join images by `relative_path`.
- Use [`metadata/TPEN_compound_reference.xlsx`](metadata/TPEN_compound_reference.xlsx) to interpret compound identifiers and treatment labels.
- Treat the final numeric suffix as the biological-replicate identifier; for example, `47-1` means compound 47, biological replicate 1.
- Use one image representation per embryo. Do not count both an SIF source image and its TIFF export as independent observations.
- TIFF files can be opened directly in Fiji/ImageJ. SIF source files may require Bio-Formats or compatible Andor acquisition software.
- Preserve the original filename and dataset-relative path in derived measurements.

## HSC quantification

The article-derived method and QC requirements are documented in [HSC-Counting Workflow](TPEN_hsc_counting_workflow.md). The paper reports ImageJ 1.53c processing with `Convolve`, followed by `Find Maxima` using noise tolerance 30 and counting within the CHT.

The article does not report the exact CHT ROI geometry or Convolve kernel. Confirm these parameters with the original laboratory before describing a reanalysis as an exact reproduction.

## Access, licence, and citation

- The associated article is open access under a Creative Commons Attribution licence.
- A separate dataset licence has not yet been confirmed and should be added to the repository record before public release.
- Cite the associated publication and, once assigned, the dataset DOI or accession. See [Citation and Attribution](TPEN_citation.md).
- Verify archive integrity using the supplied `SHA256SUMS.txt` when downloading the packaged documentation and toolkit.
