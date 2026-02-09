# Expert Review Protocol

## Goal

Review and refine the list of legal propositions (LPs) extracted from the Summary of Argument (SoA).  
Each LP should be an individual declarative statement of law that the court must adopt, resolve, or reject to reach a holding.

## Inputs

lps_audit.csv (one row per LP), containing:

- "lp_text"
- "evidence_para_ids_joined"
- "evidence_text" (full paragraph text for each evidence ID)

## Reviewer Actions (per LP)

Fill the "decision" column with one of the following values:

- **accept**: LP is correct and well-formed.
- **edit**: LP is substantively correct but requires revised wording.
- **reject**: LP is not substantive, is redundant, or lacks supporting evidence.
- **merge**: LP should be merged with other LPs expressing a similar meaning.
- **split**: LP contains multiple independent legal propositions and must be divided into atomic propositions.

## How to Complete Each Decision

### accept

- Leave "edit_lp_text" empty.
- Optionally add "notes".

### edit

- Put the revised LP wording into "edit_lp_text".
- Keep the proposition case-grounded and contestable  
  (do not over-neutralize or over-claim).

### reject

- Add a brief reason in "notes".

### merge

- Assign the same "merge_group_id" to all rows that should be merged  
  (e.g., "M01", "M02").
- The pipeline will create one finalized LP per "merge_group_id".

### split

- Put child LPs into "split_children" using the delimiter "|||".

  Example: "A ||| B ||| C"
  
- Each child should be an atomic legal proposition.
