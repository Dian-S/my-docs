# Project Context and Dataset Mapping

## Project scope

This package documents the screening images from one natural-compound project
based on a mitochondrial hydrogen-peroxide reporter in *Caenorhabditis
elegans*. It covers raw plate acquisitions and derived single-worm or
image-processing images. Numerical analysis projects, final composite images,
and later validation experiments are outside scope.

## Scientific purpose

The project uses the transgenic reporter `Pcol-19-mito(cox8)::HyPer2` to identify
natural small molecules associated with lower mitochondrial oxidative-stress
readouts in adult *C. elegans*. The reported assay readout is the ratiometric
mean-gray-value measurement `YFP500/YFP420`, calculated from paired
fluorescence channels after single-worm image extraction.

## Experimental design recorded in the supplied metadata

- organism and stage: synchronized adult Day 1 *C. elegans*;
- screen size: reported as 591 natural small molecules;
- plate format: 96-well plates, approximately 30-50 worms per well;
- treatment: 100 µM for 12 hours at 20 °C;
- imaging system: ImageXpress Pico with a 4× objective;
- channel `w1`: FITC/GFP, approximately 488 nm excitation and 525 nm emission;
- channel `w2`: DAPI/Violet, approximately 405 nm excitation;
- processing: Scellseg single-worm instance segmentation followed by ImageJ
  measurement; and
- reported assay value: `YFP500/YFP420`.

These details originate from the supplied manual metadata and should be
confirmed against the final experimental record before public release.

## Work-package mapping

| Work component | Direct supporting data | Conservative interpretation |
|---|---|---|
| Raw screening images | Eight plate-acquisition groups with paired fluorescence channels | Records the plate/well imaging input for the reported compound screen |
| Derived screening images | Single-worm and image-processing outputs | Records the image derivatives generated for per-worm quantification |

Candidate-level numerical comparisons are experimental context only and are
not themselves included as files in this image release.

## Candidate compounds

The screening summary identifies 11 candidates:

1. alpha-boswellic acid;
2. Bovinocidin / 3-nitropropionic acid;
3. acetylvanillin;
4. berberine hydrochloride;
5. chrysin;
6. epiandrosterone;
7. phloretic acid;
8. silibinin;
9. azithromycin dihydrate;
10. riboflavin; and
11. liensinine perchlorate.

Candidate spelling and identity should ultimately be reconciled against the
chemical identifiers rather than inferred from display order.

## Image-to-measurement workflow

```text
96-well compound plate
        ↓
paired whole-well TIFF acquisition (w1 and w2)
        ↓
Scellseg instance segmentation
        ↓
single-worm and processing outputs
        ↓
ImageJ mean-gray-value extraction
        ↓
YFP500/YFP420 calculation and candidate comparison
```

Raw filenames encode acquisition date, plate, well, field position, and
channel. Compound annotations are joined through the supplied L6000 workbook
using `plate_id + well_id`.

## Plate-layout interpretation

The experimental layout labels columns 1 and 12 as controls for rows A-H.
Accordingly, `A01-H01` and `A12-H12` are recorded as `compound_name=Con` and
`plate_well_status=control`. No separate `Model` wells are documented.

The L6000 table and the reported 591-compound screen do not reconcile perfectly
with the current image snapshot. Unresolved positions are therefore retained
as `unassigned`; they are not assigned a compound or control identity by
inference.

