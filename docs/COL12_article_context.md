# Project Context: COL-12 Natural-Compound Screening

## Work-package scope

This dataset documents a natural-compound screen for increased epidermal
COL-12::GFP signal in *Caenorhabditis elegans*. The release scope contains raw
whole-well acquisitions and single-worm processing images used for the screen.
Later compound-validation, transcriptional, protein, and mechanism experiments
are outside this work package.

## Associated publication

Fang J, Wu X, Meng X, Xun D, Xu S, Wang Y. Discovery of Natural Small
Molecules Promoting Collagen Secretion by High-Throughput Screening in
*Caenorhabditis elegans*. *Molecules*. 2022;27:8361.
https://doi.org/10.3390/molecules27238361

## Experimental system

The publication describes the single-copy reporter strain
`SHX3444 Pcol-19-COL-12::GFP(zjuSi337)`, in which epidermal COL-12 is visualized
with GFP. The screening workflow used:

- 614 natural compounds, each tested once at 100 µM;
- `n = 30` observations reported for the preliminary screen, with the exact
  observational unit still requiring confirmation;
- 12 h treatment at 20 °C;
- Greiner 655090 black 96-well plates;
- ImageXpress PICO high-content imaging with a 4× objective;
- Scellseg for individual-worm isolation;
- ImageJ for fluorescence measurement; and
- normalization of the control mean-gray value to 1.

The raw archive uses `w1` for FITC/GFP and `w2` for transmitted light. These
channel assignments are confirmed by the file inventory and image properties.

## Screening interpretation

The publication reports 26 compounds with increased COL-12 reporter signal in
the candidate-level display:

1. 4-Aminobutyric acid
2. Oleanolic Acid
3. Maltitol
4. Acarbose
5. Mannose
6. Sennoside A
7. L-Adrenaline
8. Fusidine
9. Danshensu
10. 10-Deacetylbaccatin III
11. Dihydrocholesterol
12. Lawsone
13. Cortodoxone
14. Baicalin
15. Sodium Danshensu
16. Betulinic acid
17. Baicalein
18. Quercetin
19. Hematoxylin
20. Shikonin
21. Isorhamnetin
22. Epicatechin
23. Plumbagin
24. Triptolide (PG490)
25. Betulin
26. Sanguinarine

Vitamin A is represented as a positive control in the supporting workbook.
`Tetracycline hydrochloride` appears as an additional analysis entry in
`final-plotting.xlsx` but is absent from the publication's 26-compound list;
it is therefore retained as an analysis-only entry rather than silently added
to the published candidates.

## Evidence boundary

The publication supports the experimental design and compound-level screening
interpretation. The image counts, paths, bit depths, resolutions, channel
assignments, and processing groups are derived from the verified data archive
and `metadata/metadata.xlsx`. Compound identities are joined from the supplied
L6000 workbook only when the available plate-and-well evidence supports them.

The final normalized measurement is not contained in the image metadata.
`contrast_std` is an image statistic and must not be interpreted as the
normalized biological screening value.
