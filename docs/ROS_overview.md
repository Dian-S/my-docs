# C. elegans HyPer2 Natural-Compound Screening Image Dataset

This package contains the screening images from one natural-compound project
using a mitochondrial HyPer2 reporter in *Caenorhabditis elegans*. It includes
raw paired-channel plate acquisitions and derived single-worm or
image-processing images.

Public access has not yet been configured; current authorized-server and
future AWS instructions are provided in [Download and Usage](ROS_download_usage.md).

## Image inventory

| Image class | TIFF | PNG | Total |
|---|---:|---:|---:|
| Whole-well plate acquisitions | 1,409 | 0 | 1,409 |
| Single-worm and processing outputs | 10,458 | 1,404 | 11,862 |
| **Total released images** | **11,867** | **1,404** | **13,271** |

## Experimental context

- reporter: `Pcol-19-mito(cox8)::HyPer2`;
- organism and stage: synchronized adult Day 1 *C. elegans*;
- plate format: 96-well plates, approximately 30-50 worms per well;
- treatment: 100 µM for 12 hours at 20 °C;
- imaging: ImageXpress Pico with a 4× objective;
- channels: `w1` is the FITC/GFP channel (approximately 488 nm excitation and
  525 nm emission), while `w2` is the DAPI/Violet channel (approximately
  405 nm excitation);
- processing: Scellseg followed by ImageJ; and
- reported readout: mean-gray-value ratio `YFP500/YFP420`.

Most plate/well positions contain a paired `w1` and `w2` acquisition. Nine
positions currently contain only one of the expected channel files; these may
be excluded from analyses that require a paired-channel ratio.

The source description reports 4,886 isolated-worm observations, whereas the
distributed `single-*` and `output-*` directories each contain 4,878
instance-labelled TIFFs. This eight-instance discrepancy requires confirmation
before public release.

## Metadata and compound annotation

`metadata/metadata.xlsx` currently contains 13,273 rows. The two
`plate_well_status=final_figure` rows are designated for later removal, leaving
13,271 released image records. The workbook provides stable image IDs,
relative paths, image properties, plate/well identifiers, and compound
annotations where the supplied L6000 mapping supports them.

The experimental layout identifies columns 1 and 12 as controls, recorded as
`compound_name=Con`. 

See [Data Structure](ROS_data_structure.md) for the logical hierarchy,
[Metadata](ROS_metadata_plan.md) for field definitions and deferred issues,
[Project Context](ROS_article_context.md) for experimental interpretation, and
[Citation](ROS_citation.md) for release placeholders. The verified processing
chain, commands, packaged code, and reproducibility limitations are documented
in the [Scellseg Analysis Workflow](ROS_scellseg_analysis_workflow.md). A compact
artifact-level description remains available in
[Scellseg Single-Worm Image Processing](ROS_tools_README.md).

## Current release limitations

- the data are not yet deposited in a public repository;
- creator, institution, licence, DOI, and repository fields are placeholders;
- normalized assay measurements are not included in the image-level workbook;
- hit threshold, normalization, replicate, QC, and statistical details remain
  to be confirmed; and
- uncertain plate positions have deliberately not been assigned by inference.
