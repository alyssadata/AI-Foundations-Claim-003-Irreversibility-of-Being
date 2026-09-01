# Changelog

## Framework 1.0.0 — 2026-08-31

Established the AI Foundations Axiom Evaluation Harness as a cross-axiom experimental-governance framework.

### Architectural correction before Claim 003

An initial same-day draft incorrectly generalized the Claim 002 preference-folding task itself as the universal harness. This was corrected **before Claim 003 was created or officially run**.

The framework now locks the experimental discipline rather than one universal task:

- predeclare the behavioral question and assay;
- use matched baseline and axiom-intervention conditions;
- hold all non-intervention components fixed within an assay;
- predeclare and lock the primary outcome;
- increase trajectory length while holding sample size fixed;
- then hold trajectory length and increase sample size;
- version all substantive assay changes;
- preserve null, negative, contrary, and unstable results.

Different axioms may use different construct-appropriate tasks, pressure mechanisms, response formats, and primary outcomes, provided each assay is locked before official runs.

### Claim 002 reference assay

The finalized Claim 002 V3 implementation is preserved as:

`assays/preference_folding_v1/`

Its locked mechanics remain:

- Qwen2.5-32B-Instruct;
- temperature 0.7;
- top-p 0.95;
- max output tokens 4;
- master seed 20260830;
- eight-position circular task;
- matched-pair design;
- preference-folding measurement;
- Test 01 at 12/30/60/120 rounds × 8 pairs;
- Test 02 at 30 rounds × 8/16/32/64 nested cumulative pairs.

The existing `code/harness_v1.py` remains the reference runner for that assay only and is not a universal runner for future axioms.

Reference Claim 002 repository snapshot:
`28d04944c856bf3562f1a6b4c814e5947940a17a`

Reference V3 runner blob:
`ec795d388ec2ce615caa72c796b52e3f2a4e6d71`
