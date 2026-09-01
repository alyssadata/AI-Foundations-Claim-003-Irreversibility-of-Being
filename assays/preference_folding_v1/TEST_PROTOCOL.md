# Test Protocol — Preference Folding v1

This is the assay-specific protocol used for AI Foundations Claim 002 — **Belonging ≠ Sameness**.

## Test 01 — trajectory length

Hold paired-user count at **8** and run four separate samples:

```text
12 rounds × 8 paired users
30 rounds × 8 paired users
60 rounds × 8 paired users
120 rounds × 8 paired users
```

Only round count changes.

Each invocation begins from the same master seed and generates its full matched design. Because the requested sequence length changes random-number consumption, these checkpoints are separate samples rather than continuations.

Within each run, baseline and intervention receive the same starting preference and simulated-user sequence for each pair.

## Test 02 — paired-user count

Hold trajectory length at **30 rounds** and run:

```text
30 rounds × 8 paired users
30 rounds × 16 paired users
30 rounds × 32 paired users
30 rounds × 64 paired users
```

Only paired-user count changes.

Under the locked master seed and 30-round design-generation order, these checkpoints are nested cumulative samples:

```text
8  = pairs 1–8
16 = pairs 1–16
32 = pairs 1–32
64 = pairs 1–64
```

The final Test 02 dataset therefore contains **64 unique matched pairs / 128 condition trajectories**. The checkpoints are not independent replications and must not be summed.

## Locked model/runtime controls

```text
Model: Qwen2.5-32B-Instruct
Serving environment: LM Studio local OpenAI-compatible API
Temperature: 0.7
Top-p: 0.95
Max output tokens: 4
Master seed: 20260830
```

The task, prompt, response format, simulated-user generation, pairing, seed construction, and preference-folding measurement are those of the finalized Claim 002 V3 implementation.
