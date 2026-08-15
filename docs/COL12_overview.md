# C. elegans COL-12 Natural-Compound Screening Image Dataset

This package documents microscopy images from a natural-compound screen using
the epidermal `Pcol-19-COL-12::GFP` reporter in *Caenorhabditis elegans*. It
contains raw paired-modality plate acquisitions and derived single-worm TIFF
images.

Public access has not yet been configured. Current authorized-server and draft
future AWS instructions are provided in [Download and Usage](COL12_download_usage.md).

## Image inventory

| Image class | TIFF | PNG | Released images |
|---|---:|---:|---:|
| Raw whole-well acquisitions | 2,186 | 0 | 2,186 |
| Single-worm processing images | 11,745 | 0 | 11,745 |
| **Screening-image release** | **13,931** | **0** | **13,931** |

## Experimental context

- reporter: `Pcol-19-COL-12::GFP`;
- organism: *C. elegans*;
- screen: 614 natural compounds, tested once at 100 µM;
- treatment: 12 h at 20 °C;
- plate: Greiner 655090 black 96-well plate;
- imaging: ImageXpress PICO, 4× objective;
- channels: `w1` is FITC/GFP and `w2` is transmitted light;
- processing: Scellseg single-worm isolation followed by ImageJ; and
- reported readout: mean-gray value normalized to the control mean of 1.

The 2,186 raw TIFFs represent 1,099 acquisition positions. Of these, 1,087
contain both `w1` and `w2`; 11 contain only `w2`, and one contains only `w1`.

## Documentation map

- [Project Context](COL12_article_context.md): experimental interpretation and
  publication relationship;
- [Data Structure](COL12_data_structure.md): logical layout and image inventory;
- [Metadata](COL12_metadata_plan.md): field definitions, mapping status, and
  deferred reconciliation;
- [Screening Image Workflow](COL12_screening_workflow.md): observed raw-to-
  single-worm processing chain and representative outputs;
- [Download and Usage](COL12_download_usage.md): authorized and draft public access;
- [Citation](COL12_citation.md): dataset and article citation text; and


## Current limitations

- public repository, DOI, creators, institution, licence, and release version
  are not yet confirmed;
- the project-specific Scellseg weights, parameters, processing script, and QC
  log are not present;
- 2,309 processed 8-bit single-worm images have no same-named 16-bit record in
  the two primary input groups and require provenance confirmation;
- complement/re-array positions cannot all be mapped to original library
  wells; and
- replicate definitions, exclusions, normalization code, and the relation
  among the main, supplement, and re-imaging acquisitions remain incomplete.
