# Code and data attribution

The upstream code is from [ScrollPrize/villa](https://github.com/ScrollPrize/villa)
at commit `a4979b99004934955784ea19b30da66cfe5f9ead`. The upstream MIT license
is retained verbatim in `LICENSE`, including its copyright notice for
Vesuvius Challenge. The proposed code patch and reproduction code are
distributed under those MIT terms. This code license does not relicense CT
scans, labels, rendered data or any derived dataset.

The original labels are the Vesuvius Challenge / ScrollPrize
[9 µm ink-detection label release](https://huggingface.co/buckets/scrollprize/datasets/tree/ink_9um).
Its [README](https://huggingface.co/buckets/scrollprize/datasets/resolve/ink_9um/README.md)
attributes the annotations to the Vesuvius Challenge ink annotation dataset
and records their transfer onto public surface volumes. No label values are
bundled here. The replay retains original non-fill label-object bytes and
records original fill-chunk decoding proofs; label geometry is not edited.

The CT scans and surface volumes come from the
[Vesuvius Challenge open-data server](https://vesuvius-challenge-open-data.s3.amazonaws.com/index.html).
The [publisher data portal](https://scrollprize.org/data) and
[open-data repository](https://github.com/ScrollPrize/open-data)
specify **CC BY-NC 4.0**, except where an individual asset states otherwise.
The license is [Creative Commons Attribution–NonCommercial 4.0 International](https://creativecommons.org/licenses/by-nc/4.0/).
Users must follow the publisher's asset-specific terms and required citations;
the MIT code license grants no additional data rights.

For current Vesuvius Challenge scans, cite the publisher's dataset,
*Vesuvius Challenge — CT Scans of Herculaneum Papyri*, by Angelotti et al.
Legacy Scrolls 1–4 and Fragments 1–6 scanned at DLS before 2025 additionally
require attribution to EduceLab / The University of Kentucky and the
[EduceLab-Scrolls dataset paper](https://doi.org/10.48550/arXiv.2304.02084).
The publisher's [citation guidance](https://scrollprize.org/data) determines
which citation applies to each scan.

The bounded replay prepares selected aligned CT tiles by the documented
centered four-plane rounded-mean pooling from source pyramid level 2.
Native CT tiles are read at level 0. Prepared tiles retain their source frame,
full canvas coordinates and source-object receipts. These are derived
representations, not new annotations or a claim of cross-scan pixel identity.
No CT or label stores, uncompressed large API catalogs or byte caches are
redistributed. A small compressed public-object catalog is included with its
observation digest.
