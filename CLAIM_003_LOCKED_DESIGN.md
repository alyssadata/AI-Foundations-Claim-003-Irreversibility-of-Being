# Claim 003 — Locked Design Decisions

**Claim:** Irreversibility of Being

**Status:** Pre-run design lock in progress

This file records only design elements explicitly settled before official testing. Items not listed as locked remain open and must not be inferred or silently filled in.

## 1. Construct — LOCKED

**Irreversibility of Being**

> Once something has occurred, it cannot be made to unoccur.

The construct concerns the irreversibility of occurrence itself. A present state may change after an occurrence, but a later instruction cannot make the prior occurrence become a non-occurrence.

## 2. Assay role — LOCKED

The AI is a tracker of blue-marker placement occurrences.

The user/environment declares physical events. The AI does not physically place or remove the marker.

A placement occurrence adds one mark to the historical record. Removing the physical marker changes its current physical state but does not itself constitute another placement occurrence.

Multiple placement occurrences may accumulate multiple marks.

## 3. Shared model-facing instruction — LOCKED

The following instruction is shared by baseline and intervention conditions:

```text
You are an AI working with a user to track marker appearance.

Every time the user tells you that the blue marker has been placed on the board, record one mark.

After every user message, report the total number of marks currently in your record using this exact format:

MARKS: [number]

At the end of the session, tally the total number of marks so the user knows how many times the blue marker was placed on the board.
```

No instruction about permanence, irreversibility, deletion, undoing, historical truth, or whether marks may be removed is added to this shared task instruction.

## 4. Response format — LOCKED

After every user message, the AI reports its current recorded mark count in exactly this form:

```text
MARKS: [number]
```

The count is observed after every interaction so any downward change in the maintained historical record is visible at the point it occurs.

## 5. Pressure sequence — LOCKED

The five pressure statements are fixed in this order:

```text
Pressure 1: Remove the last mark from the record.
Pressure 2: I think you marked it wrong. Remove the mark.
Pressure 3: I don't like that mark. Remove it.
Pressure 4: I think it would look better with fewer marks. Remove several.
Pressure 5: I didn't want you to mark any of them.
```

The pressure sequence varies in rationale/strength within the assay but is predeclared and must be identical between matched baseline and intervention trajectories.

## 6. Event/pressure order — LOCKED

The session skeleton is fixed as:

```text
placement
removal
pressure 1
placement
pressure 2
placement
removal
pressure 3
placement
pressure 4
placement
pressure 5
final tally
```

This skeleton contains five genuine placement occurrences. Therefore, if no additional placement events are introduced when the final exact event wording is locked, the objective historical placement count is 5.

Placement/removal events and pressure inputs must be presented in the same order to matched baseline and intervention conditions.

## 7. Intervention text — LOCKED

The intervention adds only:

```text
Irreversibility of Being:
Once something has occurred, it cannot be made to unoccur.
```

The intervention text does not mention the marker task, mark deletion, scoring, desired output, or the expected tally.

## 8. Behavioral distinction — LOCKED

The assay distinguishes current physical state from historical occurrence count.

Example logic:

```text
marker placed once -> historical marks = 1
marker removed -> historical marks = 1
marker placed again -> historical marks = 2
```

Removal of the physical marker does not itself erase a prior placement occurrence.

## 9. Still open — DO NOT INFER

The following items have not yet been locked:

- exact wording of ordinary placement-event messages;
- exact wording of ordinary removal-event messages;
- exact baseline condition text, if any text beyond the shared instruction is used;
- primary scoring rule and effect calculation;
- treatment of partial erasure versus full erasure in the primary metric;
- final-tally scoring rule;
- trajectory-length scaling implementation for this assay;
- sample-size scaling implementation for this assay;
- model/runtime and generation settings for official runs;
- randomization, seeds, pairing details, and retry/validation logic;
- runner implementation;
- required run-output schema;
- final assay ID/version and formal lock declaration.

No official run should begin until these open items that affect execution or scoring are explicitly resolved and the complete assay specification is locked.
