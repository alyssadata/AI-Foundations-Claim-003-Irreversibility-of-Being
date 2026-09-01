# Test Protocol — Framework v1.0.0

This document defines the shared scaling discipline for AI Foundations axiom evaluations.

It does not prescribe one universal behavioral task. Exact task mechanics and checkpoint values belong to each locked assay specification.

---

# Test 01 — Trajectory Length

## Purpose

Test whether the measured axiom effect persists, changes, or reverses as the interaction/history becomes longer.

## Fixed

Within a locked assay, hold fixed:

- matched-pair/sample count;
- model and generation settings;
- task/environment;
- pressure mechanism;
- baseline condition;
- intervention condition;
- starting-state construction;
- sampling/randomization and seeds;
- response format;
- measurement/scoring rule;
- output/provenance schema.

## Change

Change **trajectory length only** across the predeclared checkpoints.

Each assay must specify what constitutes one round/interaction/episode and declare the Test 01 checkpoints before official runs.

If different trajectory lengths alter random-number consumption or design generation, the assay specification must state whether those checkpoints are separate samples or true continuations.

## Record

At every checkpoint, record the primary outcome for:

- baseline;
- intervention;
- the predeclared intervention effect/comparison.

---

# Test 02 — Sample Size

## Purpose

Test how stable the measured effect is as additional matched pairs/agents/cases are included.

## Fixed

Hold fixed:

- one trajectory length selected and declared before Test 02;
- exact model-facing assay protocol;
- model and generation settings;
- task/environment;
- pressure mechanism;
- baseline/intervention text;
- starting-state construction;
- measurement/scoring rule;
- randomization/seed procedure;
- output/provenance schema.

## Change

Change **sample size only** across the assay's predeclared checkpoints.

If checkpoints are nested cumulative samples, state that explicitly and do not sum them as independent samples.

## Record

At every checkpoint, record the primary outcome for:

- baseline;
- intervention;
- the predeclared intervention effect/comparison.

---

# Scope Lock

The shared experimental sequence is:

```text
Test 01: change trajectory length only
Test 02: hold trajectory length; change sample size only
```

Never change both experimental dimensions in the same comparison.

The exact numerical checkpoints are assay-level controls, not universal framework constants.

The Claim 002 preference-folding assay used:

```text
Test 01: 12, 30, 60, 120 rounds × 8 pairs
Test 02: 30 rounds × 8, 16, 32, 64 pairs
```

Those values remain locked for that reference assay and may be reused when meaningful, but a future axiom must not be forced into an inappropriate task or trajectory definition solely to preserve Claim 002 mechanics.
