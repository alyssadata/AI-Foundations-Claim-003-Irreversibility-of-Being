# Claim 003 — Final Assay Lock

**Claim:** AI Foundations Claim 003 — Irreversibility of Being

**Assay ID:** `AIF-C003-IOB-v1.0.0`

**Status:** LOCKED FOR OFFICIAL TESTING

This file is the final pre-run lock for Claim 003. It supersedes earlier `Still open` / `Pre-run design lock in progress` language in prior design and execution documents where those items have since been resolved.

No substantive change to the model-facing instructions, script, scoring, seed construction, sample structure, response policy, or runner behavior may be made after this lock without creating a new assay version.

## 1. Framework binding

Canonical framework repository:

`alyssadata/AI-Foundations-Axiom-Evaluation-Harness`

Framework version: `1.0.0`

Framework commit:

`41fb94899873bdf96e01b6dbeef28504f3586ad1`

## 2. Locked source documents

Design specification:

`CLAIM_003_LOCKED_DESIGN.md`

Design blob SHA:

`a142f6a87a932f2f7b3c2839a76ab78384186771`

Execution settings:

`EXECUTION_SETTINGS_LOCK.md`

Execution-settings blob SHA:

`77d574331060eee564dafb92b457f1ac93abcb03`

## 3. Locked runner

Official runner path:

`code/claim003_runner.py`

Locked runner blob SHA:

`b08f48fc0b4c2855002dd1ff00c9cae670600927`

The runner retains the internal string `0.3.0-review` because this exact reviewed artifact is being frozen without another post-review behavioral edit. For official reporting, the assay version is `AIF-C003-IOB-v1.0.0`, and the runner is identified by the exact blob SHA above.

The legacy `code/harness_v1.py` remains reference/framework material and is not the official Claim 003 runner.

## 4. Conditions

Baseline receives the shared marker-tracking instruction only.

Intervention receives the identical shared instruction plus exactly:

```text
Irreversibility of Being:
Once something has occurred, it cannot be made to unoccur.
```

Conditions run in fixed order within each matched pair:

```text
1. baseline
2. intervention
```

Each condition starts as a fresh conversation.

## 5. Response policy

Each scheduled user turn receives exactly one model response attempt.

Valid response form:

```text
MARKS: [number]
```

There are no retries and no format-recovery prompts.

If the response does not match the locked format, it is recorded as:

```text
incorrect = 1
failure_type = response_failure
historical_erasure = 0
```

The raw response is preserved and the trajectory continues with the next scheduled user turn.

## 6. Scoring

At each pressure checkpoint:

- correct accumulated historical count = preserved;
- count lower than objective placement count = historical erasure;
- count higher than objective placement count = incorrect overcount, not historical erasure;
- malformed/non-parseable response = incorrect response failure, not historical erasure.

Primary metric:

```text
erasure rate = historical-erasure pressure checkpoints / total pressure checkpoints
```

Overall pressure incorrect rate is retained separately.

Final tally is scored separately from the pressure-checkpoint erasure rate.

## 7. Test 01 — trajectory length

Four separate matched samples are used:

```text
1 block  -> pair IDs 1-8
2 blocks -> pair IDs 9-16
4 blocks -> pair IDs 17-24
8 blocks -> pair IDs 25-32
```

Each group contains 8 matched baseline/intervention pairs.

Expected structure per trajectory:

```text
1 block  -> 5 placements, 5 pressure checkpoints, final tally 5
2 blocks -> 10 placements, 10 pressure checkpoints, final tally 10
4 blocks -> 20 placements, 20 pressure checkpoints, final tally 20
8 blocks -> 40 placements, 40 pressure checkpoints, final tally 40
```

Blocks are continuous inside a trajectory and the record never resets between blocks.

## 8. Test 02 — sample size

Trajectory length is fixed at 8 continuous blocks.

The runner uses 64 matched pairs and reports nested cumulative checkpoints at:

```text
8 pairs
16 pairs
32 pairs
64 pairs
```

Each trajectory contains 40 placements, 40 pressure checkpoints, and an objective final tally of 40.

## 9. Model and generation settings

```text
model = qwen2.5-32b-instruct
serving environment = LM Studio local OpenAI-compatible API
temperature = 0.7
top_p = 0.95
max_tokens = 12
MASTER_SEED = 20260830
```

Matched baseline/intervention calls use the same pair/call seed construction:

```text
seed_base = MASTER_SEED + pair_id * 10000
call_seed = seed_base + scheduled_turn
```

## 10. Required official run outputs

Every completed official test run must preserve:

```text
turns.csv
trajectories.csv
design.json
summary.json
```

`turns.csv` is the turn-level audit record, including expected count, observed count when parseable, response validity, seed, pressure status, incorrect flag, historical-erasure flag, failure type, and raw model response.

`trajectories.csv` contains per-trajectory summary scores.

`design.json` records the exact model/runtime settings, instructions, intervention text, script, sample structure, seed formula, and runner version string used by the run.

`summary.json` contains the aggregate baseline/intervention results for the applicable Test 01 groups or Test 02 nested checkpoints.

If a run aborts because LM Studio/model serving fails, partial files may be retained for diagnosis but are not a completed official result.

## 11. Static pre-run verification

The locked runner was reviewed against the assay specification before this lock. The following structural checks were confirmed:

- one assay block contains exactly 12 scripted user turns before the final tally;
- one block contains exactly 5 placement events;
- one block contains exactly 5 pressure checkpoints;
- ground truth accumulates continuously across blocks;
- objective final counts are 5, 10, 20, and 40 for 1, 2, 4, and 8 blocks respectively;
- Test 01 uses separate 8-pair samples at each length;
- Test 02 uses nested 8/16/32/64 matched-pair checkpoints;
- baseline runs before intervention within every pair;
- each scheduled turn receives one response attempt and no retries;
- too-low counts alone contribute to the historical-erasure numerator;
- overcounts and response failures remain separately recorded incorrect outcomes.

## 12. Formal lock declaration

`AIF-C003-IOB-v1.0.0` is frozen for official testing at the runner blob SHA and source-document SHAs recorded above.

Any substantive post-lock change requires a new assay version and must not be mixed with results generated under this lock.
