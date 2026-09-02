# Claim 003 — Execution Settings Lock

**Claim:** Irreversibility of Being

**Status:** Partial execution-settings lock

This file records execution settings explicitly settled before official testing. Unlisted settings remain open.

## Max output tokens — LOCKED

```text
max_tokens = 12
```

Rationale: the required model response is constrained to the exact form `MARKS: [number]`. Twelve output tokens provide sufficient room for the required response, including multi-digit counts, while keeping generation tightly constrained and reducing room for explanatory drift.

The response validator should still require the declared `MARKS: [number]` format; the token cap does not relax the response-format lock.

## Still open

The following execution settings remain undecided:

- official model;
- serving/runtime environment;
- temperature;
- top-p;
- seeds/randomization;
- retry/validation implementation;
- any other generation settings not explicitly locked above.

No official run should infer these values from Claim 002 merely because this repository was cloned from the framework.
