# Work structure examples

Fictional examples of the [work structure](../references/work-structure.md) conventions. Local identifiers are explanatory; reading them creates no tasks or decisions.

## One small fix

F1 removes the duplicate empty-state heading ([small fix walkthrough](small-fix.md)). It is executable and covers outcome, execution and verification, with no mandatory parent or children. Internal steps (reproduce, edit, check) stay in the same task unless real coordination or a required separate review calls for another assignment.

## Feature with independent contributions and real prerequisites

Scope: personal saved task filters, with invalid-filter behaviour still awaiting a designated decision-maker. Everything below is proposed until scope, decision and publication authority are established.

| Id | Purpose and mode | Parent | Concrete result |
|---|---|---|---|
| O1 | Outcome, group | none | Personal filters can be saved and reopened with the accepted invalid-filter behaviour and isolation |
| D1 | Decision, executable human work | O1 | Reviewed compatibility options and a recorded authorized choice |
| R1 | Investigation, executable | O1 | Evidence of the existing query representation and its limits |
| E1 | Deliverable, executable | O1 | Integrated save/reopen behaviour using the accepted choice and supported representation |
| H1 | Deliverable, executable | O1 | Help text for save/reopen, based on already settled labels |
| V1 | Verification, executable | O1 | Separate evidence against O1's accepted user-visible and isolation criteria |

Prerequisites, consumer depends on producer:

| Consumer | Producer | Required input |
|---|---|---|
| E1 | D1 | The authorized compatibility choice at its accepted revision |
| E1 | R1 | The query-representation findings used by the implementation |
| V1 | E1 | The candidate integrated behaviour and verification artifacts |
| V1 | H1 | The final help text required by O1's scope |

D1 is a task only because producing and reviewing option analysis is substantive human work; a short answer would be a mention. D1, R1 and H1 have no ordering edge; their shared parent imposes none. O1 is not an implementation assignment: E1 does not depend on O1 being done, it reads O1's accepted brief; V1 depends on concrete contributions, not on its own parent.

| O1 criterion | Contribution and evidence to inspect |
|---|---|
| Personal save/reopen round trip | E1 candidate and V1 observed behaviour |
| Accepted invalid-filter behaviour | D1 choice, E1 result, V1 case |
| Isolation between people and projects | E1 implementation and V1 adversarial evidence |
| Help text matches delivered behaviour | H1 artifact and V1 comparison |

If V1 fails isolation, E1 being done does not accept O1. A missing deployment cannot satisfy an O1 promise that includes live availability.

## Shared investigation without duplicate work

R2 serves outcomes O2 and O3. Its canonical parent is O2; O3 references it. E2 under O2 and E3 under O3 each depend on R2's specified report, so both have an explicit prerequisite; a context link from O3 alone would not block E3. If R2's report does not answer the version-specific input E3 needs, E3 stays unsatisfied and the discrepancy is reconciled. If R2 is canceled or unreadable, neither consumer invents a successful input.

## Research and decisions finish at different times

R3 (delivery evidence, see [research](research.md)) is one executable item with a report and a stop condition. It may finish with "delivery evidence exists; read evidence remains unproven". The later decision Q1 about sufficiency stays pending where it is needed. Finishing R3 does not publish the proposed implementation.

## Splitting an active item

E4 starts as a single authorized result; its worker finds that a human interaction proposal must be produced separately. Coordinate with whoever holds E4, preserve evidence and record the proposed split. E4 becomes a group by receiving subtasks, only after its worker hands off and calls `task_release`. H4 produces the accepted proposal, E5 the integrated behaviour, V4 any separately required verification. Consumer E6 keeps its prerequisite on E4 if E4 still owns the promised outcome; moving it to E5 is valid only if E5 now supplies the exact input under a recorded contract change. Editing a description does not release the assignment, and a restructuring of several edits is not atomic.

## Invalid structures and corrections

| Invalid | Why | Correction |
|---|---|---|
| E1 depends on O1's completion while O1 needs E1 | Circular completion | E1 reads the accepted brief and depends only on separately produced inputs |
| E1 depends on itself | No producer can satisfy it | Remove the edge; find the real prerequisite |
| A depends on B and B on A | Prerequisite cycle | Revisit result boundaries or supply a separately agreed input |
| Every sibling depends on the previous one | Grouping mistaken for sequence | Keep only edges justified by a required result |
| A required child is canceled, so the parent is accepted | Cancellation supplies no result | Keep the criterion unsatisfied or record an authorized replacement |
| Done children mean the outcome works | Integration evidence missing | Verify the parent against its own criteria |
| Every human question becomes a task | Overhead without separate work | Use a mention; tasks for real deliverables |
| One task copied under every beneficiary | Duplicate execution | One canonical task with explicit prerequisites and references |
| A title or label is meant to make a group untakeable | Text is not enforcement | Give it subtasks, or keep the structure in backlog or a document |
