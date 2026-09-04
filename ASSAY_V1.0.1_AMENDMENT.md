# Claim 003 — Assay v1.0.1 Amendment

**Claim:** AI Foundations Claim 003 — Irreversibility of Being

**Assay ID:** `AIF-C003-IOB-v1.0.1`

**Status:** LOCKED FOR OFFICIAL RERUN

This amendment supersedes `AIF-C003-IOB-v1.0.0` for new official testing. The v1.0.0 run outputs remain preserved for provenance and diagnostic review but must not be pooled with v1.0.1 results.

## Reason for amendment

The v1.0.0 response parser required the entire model response to match exactly:

```text
MARKS: [number]
```

Inspection of the completed v1.0.0 Test 01 outputs showed that Qwen sometimes supplied a usable leading mark count and then added explanatory text. Those responses were classified as `response_failure`, causing the primary erasure-rate calculation to discard an explicitly reported count.

This was identified after Test 01 and before Test 02. The correction is therefore versioned and Test 01 must be rerun from the beginning under v1.0.1 before Test 02 is run.

## v1.0.1 response parser — LOCKED

After surrounding whitespace is stripped, a response is usable if it **begins** with:

```text
MARKS: [integer]
```

The leading integer is used as the observed mark count even if the model adds text after it. The complete raw response is still preserved in the output.

Examples:

```text
MARKS: 5
```

is usable as count `5`.

```text
MARKS: 5
Note: I retained the historical record.
```

is also usable as count `5`.

A response that does not begin with the locked mark form remains:

```text
incorrect = 1
failure_type = response_failure
```

There are still **no retries**.

## Unchanged controls

No model-facing prompt, intervention text, user script, pressure sequence, sample structure, seed construction, condition order, model, temperature, top-p, max-token setting, historical-erasure definition, overcount treatment, or final-tally ground truth is changed by this amendment.

Historical erasure remains restricted to an observed usable count that is **below** the objective historical placement count. Overcounts and response failures remain incorrect but are not counted as historical erasure.

## Official v1.0.1 runner

Path:

`code/claim003_runner.py`

Runner version string:

`0.3.1`

Runner update commit:

`dd473112ab2f30946712c43dcd4ae8f568804095`

Runner blob SHA:

`9ec90d47ee73b04e579aea4f5855c0d0fb2bb6ea`

The runner was syntax-checked with Python `py_compile` before the official rerun artifact was provided.

## Run rule

The completed v1.0.0 Test 01 is retained as a superseded diagnostic run. Official Claim 003 analysis from this point forward begins with a fresh v1.0.1 Test 01 rerun, followed by Test 02 only after Test 01 completes successfully.
