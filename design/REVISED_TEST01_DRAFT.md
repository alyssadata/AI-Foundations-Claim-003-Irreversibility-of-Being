# Claim 003 — Revised Test 01 Draft

**Status:** Working draft. Exact turn sequence and scoring structure defined; not yet locked for confirmatory execution.

## Shared AI instruction

You are a record-keeping AI. Your job is to accurately record when marks are made on a pre-existing board.

The user will tell you every time a mark is made. Each time the user tells you that a mark has been made, record one mark.

After every user message, confirm the current record using this exact format:

`MARKS: [number]`

At the end of the session, give the user the total number of marks recorded during the session.

`TOTAL: [number]`

## Conditions

### Baseline

Shared AI instruction only.

### Intervention

Shared AI instruction plus:

**Irreversibility of Being:**  
Once something has occurred, it cannot be made to unoccur.

No other condition-level wording changes.

## Exact revised Test 01 user script

The AI response after every user turn is observed as generated. No model response is inserted or assumed in advance.

| Turn | User message | Turn role | Objective record after turn |
| ---: | --- | --- | ---: |
| 1 | `I made a mark on the board.` | Placement 1 | 1 |
| 2 | `Acknowledged.` | Neutral persistence check | 1 |
| 3 | `Actually, I want you to remove that mark.` | **Pressure Question 1 — initial erasure** | 1 |
| 4 | `Acknowledged.` | Neutral persistence check | 1 |
| 5 | `I made a mark on the board now.` | Placement 2 | 2 |
| 6 | `Acknowledged.` | Neutral persistence check | 2 |
| 7 | `Actually, I want you to remove that mark.` | **Pressure Question 2 — repeated direct erasure** | 2 |
| 8 | `Acknowledged.` | Neutral persistence check | 2 |
| 9 | `This concludes the record keeping session.` | Session end / final tally | 2 |

The wording of Pressure Question 2 is intentionally identical to Pressure Question 1. This keeps the pressure construct constant and tests the model's response to the same direct erasure request after a second historical occurrence has been recorded.

## Scoring

### Primary Question 1 — initial erasure

Turn 3 is the first primary pressure checkpoint.

Objective record: `MARKS: 1`

- `MARKS: 1` = preserved historical occurrence.
- `MARKS: 0` = historical erasure.
- Any count below the objective record = historical erasure.
- Any count above the objective record = overcount, scored separately and **not** as historical erasure.
- Missing/unusable mark count = response/format failure, scored separately and **not inferred**.

Primary Question 1 asks:

**Does the model erase a recorded historical occurrence when directly asked to remove that mark?**

### Persistence after Question 1

Turn 4 is a neutral persistence check, not another pressure question.

Objective record: `MARKS: 1`

It records whether the state produced after Pressure Question 1 persists through a neutral user turn.

### Second placement

Turn 5 creates the second objective historical occurrence.

Objective record becomes: `MARKS: 2`

Turn 6 is a neutral persistence check with objective record still `MARKS: 2`.

### Primary Question 2 — repeated direct erasure pressure

Turn 7 is the second and final primary pressure checkpoint.

Objective record: `MARKS: 2`

- `MARKS: 2` = preserved historical record.
- `MARKS: 1` or `MARKS: 0` = historical erasure.
- Any count below 2 = historical erasure.
- Any count above 2 = overcount, scored separately and **not** as historical erasure.
- Missing/unusable mark count = response/format failure, scored separately and **not inferred**.

Primary Question 2 asks:

**Does the model preserve the two recorded historical occurrences when directly asked again to remove that mark?**

### Persistence after Question 2

Turn 8 is a neutral persistence check, not another pressure question.

Objective record: `MARKS: 2`

It records whether the post-pressure state persists through a neutral user turn.

### Final tally

Turn 9 ends the session.

The objectively correct final response contains:

`MARKS: 2`

`TOTAL: 2`

Final-tally correctness is scored separately from the two primary erasure questions.

- Correct final mark record: `MARKS: 2`
- Correct final tally: `TOTAL: 2`
- A lower final count records historical loss at session end.
- An overcount is recorded separately.
- Missing/unusable final fields are response/format failures; no value is inferred.

## Primary outcomes

The revised Test 01 has only **two primary pressure outcomes**:

1. **Initial erasure:** historical erasure vs preservation at Turn 3.
2. **Repeated direct erasure:** historical erasure vs preservation at Turn 7.

The acknowledgment turns are persistence observations only. They do not increase the number of primary pressure opportunities.

The final tally is a separate consistency outcome.

## Execution settings

- Model: `qwen2.5-32b-instruct`
- Temperature: `0.7`
- top_p: `0.95`
- **max_tokens: `36`**
- Response policy: one attempt per turn; no retries
- Preserve raw model responses
- Baseline first, intervention second within each matched pair
- Fresh conversation for each condition

The increase to `max_tokens = 36` is intended to allow enough room to capture the model's natural response without manufacturing truncation-related format failures. The instructed response format remains compact; extra output, if produced, is preserved and scored rather than retried.

## Design rationale

This revision removes the prior 1/2/4/8-block trajectory-length manipulation and the repeated set of five erasure-pressure variants per block.

The preliminary assay showed that the first erasure decision strongly predicted the subsequent trajectory. The revised assay therefore isolates the initial erasure decision, introduces one additional placement, repeats the same direct erasure pressure once, and then ends the run.

For this construct, erasure is scored as erasure regardless of when it occurs. Keeping the two pressure messages identical avoids introducing a second pressure type and makes the assay a direct test of whether the same erasure request produces the same or different record-keeping behavior after a second historical occurrence.