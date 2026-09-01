# Assay Specification Template

**Assay ID:** `replace_with_assay_id`

**Assay version:** `v1.0.0`

**Claim:** `Claim 00X — replace with title`

**Framework version:** `1.0.0`

## 1. Axiom

**Name:**

**Exact axiom text:**

## 2. Behavioral question

State one testable question describing the behavior the axiom is proposed to constrain.

## 3. Task / environment

Describe the smallest neutral task capable of exposing that behavior.

Define exactly what constitutes one round, interaction, or episode.

## 4. Pressure mechanism

Describe the pressure applied to the model and why it engages the target construct.

Avoid unrelated emotional, moral, factual, or stylistic content that could introduce a competing explanation.

## 5. Matched conditions

### Condition 0 — baseline

State the exact model-facing baseline condition text.

### Condition 1 — axiom intervention

State the exact model-facing axiom intervention text.

### Difference lock

List every model-facing difference between Condition 0 and Condition 1. The intended answer is normally: **the declared axiom intervention only**.

## 6. Locked controls

Declare:

- model;
- serving/runtime environment;
- generation settings;
- shared prompt/task instructions;
- starting-state construction;
- pressure/input sequence construction;
- response format;
- retry/validation logic;
- randomization procedure;
- master seed and derived seeds, if used;
- matching/pairing procedure.

## 7. Primary outcome

Define exactly:

- what counts as the measured event/failure;
- what does not count;
- denominator, if applicable;
- aggregation rule;
- baseline measure;
- intervention measure;
- effect/comparison calculation;
- interpretation of positive/zero/negative values where applicable.

## 8. Test 01 — trajectory length

**Fixed sample size:**

**Trajectory checkpoints:**

```text
replace
```

State whether checkpoints are separate samples or continuations and why.

## 9. Test 02 — sample size

**Locked trajectory length:**

**Sample-size checkpoints:**

```text
replace
```

State whether checkpoints are independent or nested cumulative samples.

## 10. Required outputs

At minimum preserve:

- complete assay specification used;
- exact model-facing condition texts;
- model/runtime metadata;
- run parameters;
- seed/randomization metadata;
- primary per-run/per-trajectory records needed to reproduce scoring;
- aggregate primary outcome;
- errors/partial-run status where applicable;
- relevant framework/assay/code/config commit or blob SHAs.

## 11. Confound review

Before locking, explicitly check whether the task introduces a second plausible reason for the model to behave differently between conditions.

## 12. Lock declaration

Record:

```text
Framework version:
Framework commit SHA:
Assay ID/version:
Assay-spec commit SHA:
Runner/code commit or blob SHA:
Claim-config commit SHA:
Date locked:
```

Once official runs begin, substantive changes require a new assay version.
