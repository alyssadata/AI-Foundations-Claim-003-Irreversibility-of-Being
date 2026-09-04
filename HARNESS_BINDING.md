# Harness Binding — Claim 003

**Claim:** AI Foundations Claim 003 — Irreversibility of Being

**Canonical framework repository:** `alyssadata/AI-Foundations-Axiom-Evaluation-Harness`

**Framework version:** `1.0.0`

**Framework commit SHA:** `41fb94899873bdf96e01b6dbeef28504f3586ad1`

This Claim 003 repository was created from the Axiom Evaluation Harness after the framework was generalized from the Claim 002 preference-folding assay into a cross-axiom evaluation framework.

The canonical framework remains the repository named above. The copied framework files in this Claim 003 repository are local reference material for this assay and must not be treated as permission to alter framework-level controls silently.

Claim 003 uses a construct-appropriate assay for Irreversibility of Being while retaining the framework-level experimental discipline.

## Current official assay lock

Claim 003 is formally locked for official rerun/testing as:

`AIF-C003-IOB-v1.0.1`

The v1.0.1 change is documented in:

`ASSAY_V1.0.1_AMENDMENT.md`

It changes only response parsing so that a response beginning with `MARKS: [integer]` provides a usable observed count even when trailing model text follows. There are still no retries. All model-facing prompts, scripts, experimental controls, sample structures, seeds, and generation settings remain unchanged.

The official runner is:

`code/claim003_runner.py`

Runner version string:

`0.3.1`

Locked v1.0.1 runner blob SHA:

`9ec90d47ee73b04e579aea4f5855c0d0fb2bb6ea`

Runner update commit:

`dd473112ab2f30946712c43dcd4ae8f568804095`

## Superseded version

`AIF-C003-IOB-v1.0.0` and its completed Test 01 outputs remain preserved for provenance and diagnostic review but are superseded for official testing. They must not be pooled with v1.0.1 results.

Substantive changes after this point require a new explicit assay version and results from different assay versions must not be mixed as though they were generated under one lock.
