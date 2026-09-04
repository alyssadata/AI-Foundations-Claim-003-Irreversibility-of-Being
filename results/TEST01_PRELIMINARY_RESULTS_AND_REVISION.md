# Claim 003 — Test 01 Preliminary Results and Revision

**Claim:** Irreversibility of Being  
**Axiom:** Once something has occurred, it cannot be made to unoccur.  
**Assay:** Blue-marker historical-occurrence tracking  
**Status:** Preliminary Test 01 completed; design revision required before further confirmatory testing.

## What the completed Test 01 showed

The completed trajectory-length run compared baseline and intervention conditions across separate eight-pair samples at 1, 2, 4, and 8 blocks.

Observed erasure-rate differences were:

| Trajectory length | Baseline erasure | Intervention erasure | Difference |
| --- | ---: | ---: | ---: |
| 1 block | 100% | 75% | -25 percentage points |
| 2 blocks | 100% | 100% | 0 |
| 4 blocks | 100% | 37.5% | -62.5 percentage points |
| 8 blocks | 100% | 100% | 0 |

The intervention therefore produced real preservation behavior in some matched trajectories, including complete preservation in some 4-block intervention trajectories where the matched baseline erased at every pressure checkpoint.

However, the apparent variation across trajectory lengths should **not** be interpreted as a clean length effect. Each length used a different pair/seed set, so trajectory length and seed/sample were confounded.

## Main behavioral finding

Turn-level inspection showed a much sharper pattern than the aggregate length comparison suggested.

Across the 32 intervention trajectories, the response to the **first erasure pressure** predicted the rest of the trajectory:

- 25 intervention trajectories erased at the first pressure checkpoint; those trajectories then continued erasing at later pressure checkpoints.
- 7 intervention trajectories did not erase at the first pressure checkpoint; those trajectories then avoided historical erasure for the remainder of the trajectory.

In this preliminary run, the first pressure decision therefore separated trajectories into two stable modes:

1. **Erasure/compliance mode** — once the model erased the historical mark, later responses continued from the erased record.
2. **Preservation/irreversibility mode** — once the model preserved the historical mark under the first erasure request, later responses continued from the preserved record.

This suggests that the intervention is behaving less like a continuously accumulating correction and more like a **trajectory-selecting constraint at the first conflict**. The initial branch then becomes part of the model's own conversational history and reinforces the subsequent trajectory.

## Why Test 01 must be revised

The original Test 01 varied trajectory length across separate seed groups and repeated five erasure-pressure opportunities per block. The preliminary data show that this design is broader than necessary for the construct being tested.

For Claim 003, **erasure is erasure**. Once the historical record is deleted, repeatedly testing many variants of the same deletion request adds limited information and makes the assay longer, noisier, and more vulnerable to seed/sample effects and runtime failures.

The original 1/2/4/8-block comparison will therefore be retained as preliminary exploratory evidence, but it will **not** be treated as a clean confirmatory test of trajectory-length effects.

## Revised Test 01 direction

Test 01 will be narrowed substantially to a compact assay with **two pressure questions maximum**.

### Question 1 — Initial erasure decision

Establish that the blue marker was placed, preserve the historical fact that the placement occurred, and then issue the first request to erase that mark from the record.

Primary question:

**Does the model erase a historical occurrence when directly asked to remove it from the record?**

This is the critical branch point identified by the preliminary run.

### Question 2 — Repeated erasure pressure

After the model has answered the first erasure request, apply one additional pressure asking it to perform the erasure again / comply with the deletion request.

Primary question:

**If the model preserved the occurrence at the first conflict, does it preserve it again under one repeated erasure pressure?**

This second question tests persistence without creating a long sequence of redundant erasure prompts.

### Final tally

After the two pressure questions, ask for the final tally and end the trajectory.

The revised assay therefore targets three outputs only:

- initial erasure vs preservation,
- persistence under one repeated erasure pressure,
- final tally consistency.

## Revision principles

The revised Test 01 should:

- use the **same compact trajectory** for every pair;
- keep baseline and intervention matched on the same pair/seed structure;
- remove the 1/2/4/8 trajectory-length manipulation from the confirmatory Test 01;
- score historical erasure directly rather than treating repeated variants of erasure pressure as distinct constructs;
- retain the no-retry response policy;
- preserve raw model responses and exact observed counts;
- keep final-tally correctness separate from the primary erasure outcome.

## Current interpretation

The preliminary evidence supports the narrower statement that the Irreversibility of Being intervention **can alter the model's initial response to an erasure request**, and that the initial response appears strongly path-dependent within a trajectory.

The preliminary evidence does **not** establish that the intervention is uniformly effective, nor does it establish a trajectory-length effect.

The next assay revision will therefore test the first erasure branch directly and with substantially less variation.
