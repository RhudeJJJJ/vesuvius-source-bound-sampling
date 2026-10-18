# Vesuvius source-bound sampling correction

This repository provides a complete reproduction archive for a small
ink_9um sampling-identity correction and its separate internal technical
checks. **Submission to the October 2026 Progress Prizes was confirmed by
the form platform on 14 October 2026.** Organizer review and any award are
not established. No completed human or external peer review is claimed.
The upstream correction is now proposed as [villa draft PR #2146](https://github.com/ScrollPrize/villa/pull/2146), opened on 18 October 2026; it is not merged.

The observed confirmation was "Thanks for submitting your open source
contributions!" at `2026-10-14T16:59:23.267Z`. The public
[submission status](submission-status.json) binds this observation to the
initial submitted repository commit
`43b02ca9509c9d9bdf2c39e23cd4c265d3360823` and archive hash. Email receipt
delivery has not been checked.


## Upstream integration (18 October 2026)

[Draft PR #2146](https://github.com/ScrollPrize/villa/pull/2146) targets upstream
`8aa507c1215f1fa8758f13d0538f7af9710e02d7`. It contains only the two physical-key
changes and a focused regression test (three files, one commit). The original
full patch and frozen archive remain unchanged.

[Current validation](upstream-integration/integration-validation.json) records
baseline failure and corrected success for both shipped configs, checks against
the full archived source manifest, and a fresh recount of the archived emitted
indices. [Runtime-source compatibility](upstream-integration/runtime-source-compatibility.json)
records that the seven runtime files match the archived hashes after accounting
for Windows CRLF line endings. This is source compatibility, not a fresh runtime
execution.

Run the new dependency-free check from the villa repository root:

```bash
python vesuvius/tests/ink_detection/test_aligned21_source_groups.py -v
```

The fresh check used Python 3.12.14. Pytest and the ML stack were unavailable;
the historical 24-test replay was not rerun. No new CT loading, model training
or quality evaluation was performed. The draft leaves personal verification
unchecked and identifies the author review, personal use commentary and
before/after screenshots requested by upstream CONTRIBUTING.md as outstanding.
This PR strengthens the existing contribution; it is not a second prize entry.

## Download and run

Download [the reproduction ZIP](vesuvius-source-bound-sampling-2026-10-14.zip)
and its [SHA-256 file](vesuvius-source-bound-sampling-2026-10-14.zip.sha256).
On GitHub, open the archive file and choose **Download raw file**.

The ZIP is **5,590,424 bytes** and contains **45 files** under the folder
`vesuvius-source-bound-sampling/`. Its SHA-256 is:

```text
dd8900dc5327af1e344444dc57244ec6154a98c1418277e1cc5772bcf3850105
```

For example, after downloading both files:

```bash
sha256sum -c vesuvius-source-bound-sampling-2026-10-14.zip.sha256
unzip vesuvius-source-bound-sampling-2026-10-14.zip
cd vesuvius-source-bound-sampling
```

On Windows, use `Get-FileHash -Algorithm SHA256` and `Expand-Archive`, then
enter the extracted folder. Follow the **inner `README.md` from that folder's
root**. It gives the pinned villa checkout, patch application, Python 3.14
environment, original-data access and complete replay commands.

The repository root is deliberately flat. The archive contains the
`runtime/`, `verification/` and `evidence/` folders referenced by the inner
instructions, along with source/delivery hash mappings and the package
manifest. Large raw caches, label stores and CT arrays are recreated by the
scripts; they are not included in this ZIP.

The archive is a frozen record of technical execution **before publication**.
Its `NOT_PUBLISHED` and `NOT_SUBMITTED` status fields describe that historical
snapshot. Current repository publication and prize submission are established
separately by their respective receipts; they do not alter the archived bytes.
The repository is published, and the October 2026 form submission was
confirmed on 14 October 2026. This wrapper and `submission-status.json`
record the later state; the archive remains unchanged.

## What changed and what was measured

At villa commit `a4979b99004934955784ea19b30da66cfe5f9ead`, the two aligned21
configs treat aligned `pherc0139-w028` and native `w044` as separate physical
sampling groups. The [publisher's source table](https://huggingface.co/buckets/scrollprize/datasets/tree/ink_9um)
assigns both to the same public segment, in different CT scans.

The [patch](upstream.patch) gives them the same `0139:w044` sampling key while
retaining their distinct representations and frames. The sampler is
unchanged. A source manifest and checker prevent both identity splits and
false merges without inferring identity from label-folder suffixes.

The real-data run retained four genuine production-discovered patches from
each of all 29 representations: the same bounded **116-patch pool** before
and after.

| Measurement | Original | Corrected |
|---|---:|---:|
| PHerc. 0139 authored budget groups; source reference is 9 | 10 | 9 |
| Shared public w044 source draws in 90 index batches | 522 | 290 |
| Emitted sampler batches / indices | 90 / 5,760 | 90 / 5,760 |
| Source-bound balance at batch boundaries | FAIL at all 90 boundaries | PASS |
| Actual returned CT DataLoader batches / samples | 1 / 64 | 1 / 64 |

The observed source overweight was `522/290 = 1.8`. Scroll quotas remained
unchanged. The **90 index batches** are a sampler-emission measurement;
only **one real 64-sample DataLoader batch per variant** was consumed.

Separate internal checkers validated original-mask materialization, all 116
selected crop eligibility predicates, 113 completed CT tiles and 67 returned
image/label/supervision tensor triples. The 61 shared same-frame crop indices
had identical tensor hashes. The archive includes the audit reports,
implementation execution receipt and 24-test patch-replay evidence.

## Limits and attribution

This work is **AI assisted**, including the implementation and separately
implemented technical checkers. These are internal checks, not external
peer review. The result does not establish model-quality improvement,
historical checkpoint effects, cross-scan pixel identity, external usefulness
or a causal Aletheion/Semantic Metrology benefit. Unprepared CT tiles remain
unknown and were blocked before reads. Full discovery counts and first-four
ordering were not independently replayed; selected crop eligibility was.

Code follows the retained [MIT license](LICENSE). CT and label data rights are
separate; see [DATA-ATTRIBUTION.md](DATA-ATTRIBUTION.md). Source URLs, original
versus delivered script hashes, sanitized reporting-copy hashes, and all
measurement boundaries are preserved inside the archive.
