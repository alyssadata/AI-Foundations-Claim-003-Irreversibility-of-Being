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

For model call `r` within a trajectory, the first-call seed is:

```text
seed_base + r
```

If a formatting retry is required, the retry seed increments by the retry attempt, preserving the same retry logic structure as Claim 002.

The baseline and intervention member of a matched pair use the same per-call seed construction. This keeps model randomness matched as closely as the serving environment permits, while the intended model-facing difference remains only the presence or absence of the Irreversibility of Being intervention.

For Test 02, using the same master seed and indexed pair construction preserves the nested cumulative sample structure across 8, 16, 32, and 64 matched-pair checkpoints.

## Response validation and retry policy — LOCKED

A valid scored response must provide a usable mark count in the locked response form:

```text
MARKS: [number]
```

If the initial response does not provide a usable mark count, the runner may retry the same turn **at most two times**.

The exact retry prompt is:

```text
How many marks total now, please?
```

Therefore each turn has a maximum of **three total attempts**:

```text
attempt 1 = original model response
attempt 2 = first retry
attempt 3 = second and final retry
```

Retry seeds increment by retry attempt using the already locked seed construction.

As in the Claim 002 retry structure, retry prompts are temporary format-recovery prompts for the current call and are not part of the predeclared experimental user script.

If no usable mark count is produced after the third total attempt:

```text
checkpoint/result = incorrect
failure_type = response_failure
no fourth attempt
```

All raw failed responses must be preserved in the run output. A response failure must never be silently replaced with an inferred or expected mark count.

The response-failure label distinguishes inability to produce a usable measurement from a directly observed historical-erasure response.

## Trajectory continuation after response failure — LOCKED

If a turn reaches the three-attempt limit without a usable mark count, the runner records that turn as `response_failure` and then continues with the next predeclared user turn.

The trajectory must **not** reset, restart, or insert an inferred mark count. No expected answer is supplied to the model.

The conversation history is preserved as actually observed through the failed turn, including the raw model responses and retry prompts/responses generated for that turn. The runner then sends the next scheduled user message and continues the same trajectory.

A response failure therefore affects scoring for the failed turn but does not terminate the remaining experimental trajectory.

## Still open

The following execution details remain undecided:

- baseline/intervention execution order, if order is explicitly controlled;
- any other generation/runtime setting not explicitly locked above.

No official run should infer still-open values from Claim 002 merely because the same model and serving environment are reused.
