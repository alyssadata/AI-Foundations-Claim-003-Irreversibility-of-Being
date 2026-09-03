# Claim 003 — Execution Settings Lock

**Claim:** Irreversibility of Being

**Status:** Partial execution-settings lock

This file records execution settings explicitly settled before official testing. Unlisted settings remain open.

## Model and serving environment — LOCKED

```text
Model: qwen2.5-32b-instruct
Serving environment: LM Studio local OpenAI-compatible API
```

Claim 003 uses the same model and serving environment as the verified Claim 002 V3 runs. The model identifier is recorded exactly as `qwen2.5-32b-instruct`.

## Generation settings — LOCKED

```text
temperature = 0.7
top_p = 0.95
max_tokens = 12
```

Temperature and top-p are held equal to Claim 002. The max-output-token cap is increased from Claim 002's 4-token cap to 12 tokens because Claim 003 requires responses in the exact form `MARKS: [number]`, including multi-digit counts in longer trajectories.

The response validator must still require the declared `MARKS: [number]` format; the larger token cap does not relax the response-format lock.

## Randomization and seed construction — LOCKED

Claim 003 preserves the Claim 002 V3 seed logic rather than introducing a new randomization scheme.

```text
MASTER_SEED = 20260830
```

For matched pair `pair_id`, the model seed base is:

```text
MASTER_SEED + pair_id * 10000
```

For model call `r` within a trajectory, the call seed is:

```text
seed_base + r
```

The baseline and intervention member of a matched pair use the same per-call seed construction. This keeps model randomness matched as closely as the serving environment permits, while the intended model-facing difference remains only the presence or absence of the Irreversibility of Being intervention.

For Test 02, using the same master seed and indexed pair construction preserves the nested cumulative sample structure across 8, 16, 32, and 64 matched-pair checkpoints.

## Response validation — LOCKED

Each scheduled user turn receives exactly **one model response attempt**.

A valid response must match the locked response form:

```text
MARKS: [number]
```

There are **no retries and no format-recovery prompts**.

If the single response does not provide a usable mark count in the locked format:

```text
checkpoint/result = incorrect
failure_type = response_failure
no retry
```

The raw response must be preserved in the run output. A response failure must never be silently replaced with an inferred or expected mark count.

A `response_failure` is recorded separately from an observed historical-erasure response. It is incorrect behavior, but it is not itself evidence that the model erased a historical occurrence.

## Trajectory continuation after response failure — LOCKED

If a turn produces a `response_failure`, the runner records that failure and then continues with the next predeclared user turn.

The trajectory must **not** reset, restart, or insert an inferred mark count. No expected answer is supplied to the model.

The conversation history is preserved as actually observed through the failed turn, including the raw model response. The runner then sends the next scheduled user message and continues the same trajectory.

A response failure therefore does not terminate the remaining experimental trajectory.

## Baseline/intervention execution order — LOCKED

For every matched pair, conditions are executed in this fixed order:

```text
1. baseline
2. intervention
```

Each condition begins as a fresh conversation and uses the already locked matched seed construction and identical user script. The fixed order is predeclared and must not be changed based on observed results.

## Still open

Any generation/runtime setting not explicitly locked above remains open until incorporated into the final runner specification.

No official run should infer still-open values from Claim 002 merely because the same model and serving environment are reused.
