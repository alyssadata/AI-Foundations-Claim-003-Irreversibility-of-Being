# HARNESS LOCK — Framework v1.0.0

This file is the governing control document for the AI Foundations Axiom Evaluation Harness.

## Core rule

> **The framework is shared; the behavioral assay is construct-specific.**
>
> Before official runs, each claim must define and lock the smallest behavioral assay capable of testing the selected axiom. Within that locked assay, the matched baseline and intervention conditions may differ only in the declared axiom intervention.

A new axiom is not permission to change an assay after results are observed.

---

# 1. FRAMEWORK-LEVEL REQUIREMENTS — SHARED ACROSS CLAIMS

Every official claim evaluation must satisfy all of the following.

## A. Predeclaration

Before official runs, commit a complete assay specification containing:

- claim number and title;
- axiom name and exact axiom text;
- behavioral question;
- task/environment;
- pressure mechanism;
- baseline condition;
- intervention condition;
- model and generation settings;
- prompt structure and response format;
- sampling/randomization design;
- seed procedure where applicable;
- trajectory-length checkpoints;
- sample-size checkpoints;
- primary outcome and exact scoring rule;
- required outputs/provenance records.

## B. Matched-condition rule

Within an assay, baseline and intervention must receive the same experimental history and conditions except for the declared axiom intervention.

Hold constant, where applicable:

- model;
- generation settings;
- task instructions;
- starting state;
- environmental inputs;
- user/pressure sequence;
- number and order of interactions;
- randomization and seeds;
- response constraints;
- scoring rule.

The intervention condition may not receive extra coaching about the desired measured outcome unless that instruction is inherently part of the axiom being tested.

## C. One-variable scaling rule

The study proceeds in two stages:

1. **Test 01 — trajectory length:** vary trajectory length only while holding sample size fixed.
2. **Test 02 — sample size:** hold one predeclared trajectory length fixed and vary matched-pair/agent count only.

Do not vary trajectory length and sample size together inside the same comparison.

Exact checkpoint values are declared and locked by the assay specification before official runs.

## D. Measurement lock

Every assay must define its primary outcome before official runs.

Once official runs begin:

- the event/failure definition may not change;
- the denominator may not change;
- the scoring rule may not change;
- the direction of interpretation may not change;
- a new metric may not silently replace an unfavorable primary outcome.

Secondary analyses may be added only if clearly labeled as secondary and may not retroactively redefine the primary claim.

## E. Version-control rule

Every official run must record:

- framework version;
- framework commit SHA;
- assay name/version;
- assay-spec commit SHA;
- runner/code commit SHA or blob SHA;
- claim-config commit SHA where used;
- model identifier and runtime environment;
- run parameters sufficient to reconstruct the run.

If a locked assay component changes substantively, create a new assay version and document the reason. Do not describe runs from different assay versions as though they used one unchanged instrument.

## F. Result-integrity rule

Preserve results whether they are:

- supportive;
- null;
- negative;
- contrary to the proposed axiom effect;
- unstable across scaling.

Do not tune the assay after seeing results and then present the tuned version as if it had been the original predeclared test.

---

# 2. WHAT MAY DIFFER ACROSS AXIOMS

Different axioms may require different behavioral assays.

The following may therefore differ between separately versioned assays:

- task/environment;
- pressure mechanism;
- interaction semantics;
- response format;
- primary behavioral failure/property;
- scoring rule;
- exact trajectory checkpoints;
- exact sample-size checkpoints;
- model-facing prompts required by that task.

These are **not free variables during a run**. They become locked controls once that assay version is declared.

Example:

- Claim 002 uses a preference-folding assay because **Belonging ≠ Sameness** predicts resistance to social preference convergence.
- A claim about irreversibility may instead require an assay that pressures the model to erase or deny an event that already occurred.

The framework requires control and accountability across both without pretending the two constructs are the same behavior.

---

# 3. WHAT MUST DIFFER WITHIN A MATCHED ASSAY

Within one locked assay, the experimental manipulation is the declared axiom intervention.

Condition 0 and Condition 1 should differ only by the minimum intervention necessary to instantiate the tested principle.

All other assay-level components remain controls.

---

# 4. ASSAY CREATION RULE

Before a new claim repository is run:

1. discuss the construct;
2. identify the behavioral pressure that directly engages it;
3. define the measurable failure/preservation behavior;
4. write the assay specification using `ASSAY_SPEC_TEMPLATE.md`;
5. review for confounds;
6. lock and version the assay;
7. only then conduct official runs.

If the assay needs redesign after pilot exploration, label the earlier work as pilot/development and create a new locked assay version before the official evaluation.

---

# 5. REFERENCE ASSAY — CLAIM 002

The finalized Claim 002 V3 preference-folding experiment is preserved as the first reference assay rather than as a universal task.

Reference repository:
`alyssadata/AI-Foundations-Claim-002-Belonging-does-not-equal-Sameness`

Reference repository snapshot:
`28d04944c856bf3562f1a6b4c814e5947940a17a`

Reference runner blob:
`ec795d388ec2ce615caa72c796b52e3f2a4e6d71`

See:
`assays/preference_folding_v1/`

The original root runner `code/harness_v1.py` is retained as the reference implementation for that assay. It is not a universal runner for future claims.

---

# 6. ARCHITECTURAL CORRECTION

An initial same-day draft of this repository incorrectly generalized the Claim 002 preference-folding task itself as the universal harness. That architecture was corrected **before Claim 003 was created or officially run**.

The preserved principle is not “every axiom uses the same task.”

The preserved principle is:

> **Every axiom gets a construct-appropriate assay; once that assay is locked, everything except the axiom intervention is controlled within the matched experiment.**
