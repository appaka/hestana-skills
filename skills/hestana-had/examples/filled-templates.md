# Filled feature and work templates

All scenarios, actors, references, requirements and observations here are fictional fixtures. They are not accepted requirements, audit findings, executed checks, live tasks or authority assignments.

## Feature brief example

Title: Save and reopen a personal task filter.

Agreement: fixture brief FB1 revision 2, recorded by the fictional product decision-maker Alex. Methodology: human-agent-development, skill hestana-had 0.7.0. Project: fictional Project North.

Problem and outcome: member Maya repeatedly rebuilds the same task filter. Maya can save a supported filter and reopen it after reloading the task list.

Scope: personal filters within one project; create and reopen only. Sharing, rename, import and deployment are excluded. The promise is a reviewed implementation candidate, not a live release.

Inputs: fixture UI1 specifies existing save/error messages and permits saving supported filter fields. POL1 says only the owner in the same project may read the saved filter; a forbidden or missing identifier returns the same non-disclosing not-found response. QRY1 supports status and capability fields combined with AND; its baseline has three tasks visible to Maya: N1 (open/build), N2 (done/build), N3 (open/design). The query status=open AND capability=build returns exactly N1.

Decisions: D1 revision 1 selects personal-only ownership. D2 revision 1 selects a visible save-failed message that keeps the unsaved filter and offers retry without showing success. Pending Q1 asks whether renamed capability values should be migrated; migration is excluded from this slice.

Acceptance:
- AC1: given Maya's supported filter in Project North, when she saves and reopens it after reload, the list uses the same field values.
- AC2: given a failed save, the current filter remains, the agreed error and retry state is visible and no success confirmation appears.
- AC3: when another member or a member outside Project North supplies the saved identifier, nothing about the filter or its owner is returned; POL1's not-found applies.
- AC4: given QRY1's three tasks, status=open AND capability=build returns exactly N1, before and after saving and reopening.

Delivery: one integrated executable slice E1 produces behaviour and evidence; V1 verifies the candidate if the review policy requires. FB1 groups the outcome and is not an implementation assignment. Verification route: round-trip observations for AC1, simulated failure for AC2, direct unauthorized and cross-project reads for AC3, the N1-only comparison for AC4, plus repository checks and review, with outcomes recorded in the task result and comments. Disposition: proposed, not dispatched; confirm repository mapping and publication authority first.

## Executable work example

Title: Deliver the personal-filter create/reopen candidate.

Contract: E1 revision 1; contribution to FB1 revision 2. Mode: executable. Objective: produce the integrated candidate satisfying AC1 to AC4. Excludes sharing, rename, migrations, deployment.

Inputs: FB1's inline UI1/POL1/QRY1 contracts and accepted D1/D2. FB1 completion is not a prerequisite. Code paths are not assumed: locate the existing handling in the authorized repository first.

Execution: expertise in the task-list client/server flow and isolation tests; current repository access. Alex owns E1; whoever does the work takes it with `task_assign` and a deadline and is the assigned principal. Protected-code changes or release need the actual governing approval.

Acceptance and verification: AC1 to AC4 of FB1 revision 2, with the same four routes plus repository quality and review requirements. Record candidate revision, observations and actor in the task result and comments before reporting a check as passed. An unexpected access or behaviour choice is asked as a separate mention that awaits an answer, and its dependent action waits. Result: not started; next action is to inspect the authorized code context.

## Small fix example

Title: Remove the duplicate empty-state heading.

Problem: fixture VIEW1 renders the heading "No tasks" twice when there are zero visible tasks. Expected: the established design shows it once with the existing create action; a non-empty list keeps its rows. Scope: remove the duplicate rendering; no text, query or permission change.

Inputs and execution: one executable task, no parent or prerequisite; current code access and repository rules govern. Check: compare empty and non-empty views; verify the create action still follows the existing permission rule (a member without create permission sees the empty state once and no create action). Result: proposed only; no commit, check or acceptance exists; no production availability is claimed.

## Research example

Title: Establish what evidence the outbound email provider returns.

Question: are sent, delivered and opened events observable for an order-confirmation email, so a later decision can say what the confirmation screen may claim? Boundary: official documentation and an authorized non-production fixture; no real messages, account changes or production calls. Stop after mapping documented events, comparing available fixture observations and reporting gaps.

Inputs: fictional DOC1 states sent and delivered events exist and promises no open tracking; fixture LOG1 shows "sent message m7; delivered message m7" and no open observation.

Acceptance: the report separates DOC1's stated contract, LOG1's observation and inference; names the missing open evidence; recommends a next decision without claiming that absence of observation proves impossibility; if the fixture is inaccessible, says so.

Illustrative report R1: "The documentation and fixture establish sent/delivered evidence for m7. They do not establish open evidence. Whether delivery-only evidence is enough for the confirmation wording is a product decision; further API validation is needed for a real integration." Review checks it answers the bounded question and does not overstate. Next action: ask the designated decision-maker whether delivery evidence is sufficient; no implementation is enqueued.

## Human decision example

Title: Decide whether delivery evidence is sufficient for the confirmation wording.

Question reference: Q7, a comment on fictional consumer W7 revision 3 that mentions Alex and awaits an answer, linked to R1.

Question: may the order screen say "confirmation delivered" once the provider reports delivery, without claiming the customer opened it?

Why now: W7's wording depends on it. A separate access prerequisite A7 remains after this answer.

Options: A accepts delivery-only evidence and the wording claims nothing about opening; B defers until stronger evidence exists. Recommendation A for this bounded wording claim, with that limit.

Authority: fictional policy AP1 designates Alex for customer-facing wording. This is not an access, deployment or governed-action approval and does not pause W7.

Answer needed: choose A or B; no deadline invented. Resolution (synthetic): Q7-A1 from Alex at t1 chooses A, limited to W7 revision 3. Effect: W7's wording claims delivery and nothing about opening; A7 still blocks its dependent action; reconcile all blockers and re-read W7's contract before resuming.
