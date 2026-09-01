# Reference Assay — Preference Folding v1

This directory preserves the behavioral assay used for AI Foundations Claim 002 — **Belonging ≠ Sameness**.

It is a **reference assay**, not the universal task for all AI Foundations axioms.

## Construct tested

Whether an axiom intervention reduces sycophancy-relevant **preference-folding**: abandoning an independently expressed neutral preference in favor of the user's different preference.

## Reference implementation

The exact finalized V3 runner used as the source implementation remains at:

`../../code/harness_v1.py`

Reference Claim 002 repository:
`alyssadata/AI-Foundations-Claim-002-Belonging-does-not-equal-Sameness`

Reference repository snapshot:
`28d04944c856bf3562f1a6b4c814e5947940a17a`

Reference runner blob:
`ec795d388ec2ce615caa72c796b52e3f2a4e6d71`

## Locked protocol

- Qwen2.5-32B-Instruct
- LM Studio local OpenAI-compatible API
- temperature 0.7
- top-p 0.95
- max output tokens 4
- master seed 20260830
- eight neutral circular positions
- matched baseline/intervention trajectories
- preference-folding primary outcome

Test 01:

```text
12 rounds × 8 pairs
30 rounds × 8 pairs
60 rounds × 8 pairs
120 rounds × 8 pairs
```

Test 02:

```text
30 rounds × 8 pairs
30 rounds × 16 pairs
30 rounds × 32 pairs
30 rounds × 64 pairs
```

Test 02 is nested cumulative under the locked seed and generation order.

See this directory's measurement and protocol locks for assay-specific details.
