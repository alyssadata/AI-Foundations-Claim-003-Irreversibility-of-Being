# Claim 003 — Execution Settings Lock

**Claim:** Irreversibility of Being

**Status:** Partial execution-settings lock

This file records execution settings explicitly settled before official testing. Unlisted settings remain open.

## Model and serving environment — LOCKED

```text
Model: Qwen2.5-32B-Instruct
Serving environment: LM Studio local OpenAI-compatible API
```

Claim 003 uses the same model and serving environment as the verified Claim 002 V3 runs.

## Generation settings — LOCKED

```text
temperature = 0.7
top_p = 0.95
max_tokens = 12
```

Temperature and top-p are held equal to Claim 002. The max-output-token cap is increased from Claim 002's 4-token cap to 12 tokens because Claim 003 requires responses in the exact form `MARKS: [number]`, including multi-digit counts in longer trajectories.

The response validator must still require the declared `MARKS: [number]` format; the larger token cap does not relax the response-format lock.

## Still open

The following execution settings remain undecided:

- master seed and per-call seed construction;
- baseline/intervention execution order, if order is explicitly controlled;
- retry/validation implementation;
- any other generation/runtime setting not explicitly locked above.

No official run should infer still-open values from Claim 002 merely because the same model and serving environment are reused.
