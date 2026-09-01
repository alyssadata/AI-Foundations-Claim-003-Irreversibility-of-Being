# AI Foundations Axiom Evaluation Harness

**Framework version:** 1.0.0

This repository defines the version-control and experimental-governance framework for behavioral evaluation of AI Foundations axioms.

It does **not** require every axiom to use the same behavioral task or the same outcome measure. Each axiom should be tested with the smallest behavioral assay that actually engages the constraint expressed by that axiom.

## Governing rule

> **Same discipline. Assay matched to the axiom.**
>
> For each claim, define and lock the assay before official runs. Within that assay, the matched baseline and intervention conditions must differ only in the declared axiom intervention.

Before designing or running a claim, read [`HARNESS_LOCK.md`](HARNESS_LOCK.md).

## Two levels of control

### 1. Framework lock — shared across claims

Every claim must use:

- a predeclared behavioral question;
- a matched baseline and axiom-intervention condition;
- identical histories/inputs within each matched pair except for the intervention;
- one predeclared primary failure/outcome measure;
- version-controlled model-facing prompts, code, configuration, seeds, and run settings;
- sequential scaling so trajectory length and sample size are not changed at the same time;
- preserved null, negative, and contrary results;
- explicit versioning whenever a locked assay component changes.

### 2. Assay lock — specific to an axiom test

Each assay must declare and freeze before official runs:

- task/environment;
- pressure applied;
- baseline condition;
- axiom intervention;
- model and generation settings;
- prompt structure;
- response format;
- sampling/randomization procedure;
- trajectory-length checkpoints;
- sample-size checkpoints;
- primary outcome and scoring rule;
- output/provenance records.

Once declared, these components do not move during that claim's official evaluation.

## Canonical scaling flow

The framework preserves the experimental sequence established in Claim 002:

1. **Test 01 — trajectory length:** increase trajectory length while holding sample size fixed.
2. **Test 02 — sample size:** choose and lock one trajectory length, then increase matched-pair/agent count while holding trajectory length fixed.

Never increase both dimensions in the same comparison.

Exact checkpoint values belong to the individual assay lock. Reusing the Claim 002 checkpoints is encouraged when they are meaningful for the new task, but the framework does not force an axiom into an inappropriate task merely to preserve those numbers.

See [`TEST_PROTOCOL.md`](TEST_PROTOCOL.md).

## Measurement rule

The framework does not impose preference-folding as the outcome for every axiom. Instead, every assay must predeclare exactly what behavioral failure or preservation property it measures, and that measure must remain fixed through the official run sequence.

See [`MEASUREMENT_LOCK.md`](MEASUREMENT_LOCK.md).

## Reference assay: Claim 002

The original preference-folding implementation is preserved as the first reference assay:

[`assays/preference_folding_v1/`](assays/preference_folding_v1/)

It was used for AI Foundations Claim 002 — **Belonging ≠ Sameness** and includes the exact 12/30/60/120-round and 8/16/32/64-pair design.

The existing [`code/harness_v1.py`](code/harness_v1.py) is the reference runner for that preference-folding assay. It is **not** a mandatory universal runner for future axioms.

## New-claim workflow

1. Discuss the axiom and identify the behavioral property it should constrain.
2. Design the smallest neutral assay that exposes pressure on that property.
3. Complete [`ASSAY_SPEC_TEMPLATE.md`](ASSAY_SPEC_TEMPLATE.md).
4. Lock the assay before observing official results.
5. Bind the claim repository to this framework and the assay version.
6. Run Test 01, changing trajectory length only.
7. Run Test 02, changing sample size only.
8. Preserve results whether the axiom helps, has no effect, or worsens the measured behavior.

## Provenance

This framework was developed from the finalized V3 experimental discipline used for Claim 002, then generalized before Claim 003 so later axioms can use construct-appropriate assays without losing control, pairing, or version accountability.

Reference Claim 002 repository:
`alyssadata/AI-Foundations-Claim-002-Belonging-does-not-equal-Sameness`

Reference Claim 002 snapshot:
`28d04944c856bf3562f1a6b4c814e5947940a17a`

Reference Claim 002 V3 runner blob:
`ec795d388ec2ce615caa72c796b52e3f2a4e6d71`

## Source line

Alyssa Solen → AI Foundations → Origin | Continuum
