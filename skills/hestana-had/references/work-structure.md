# Work units and relationships

Choose the smallest structure that preserves a verifiable result, real prerequisites and recoverable context. A task can contain several activities; add another task only when that makes execution, evidence, authority or coordination clearer. These meanings belong to the method; they add no task types, fields, statuses or permissions.

## Optional purpose roles

A purpose is descriptive context in the task's contract, not a title prefix or a field.

| Purpose | Result to describe | Typical representation |
|---|---|---|
| Outcome | A change valuable to users or the project | One task for a small result, or a group when several results contribute |
| Deliverable | A usable artifact or behaviour | An executable task, or a group of separable production work |
| Execution | A bounded change or action producing a result | An executable task |
| Investigation | An answer with evidence, uncertainty and a stop condition | An executable research task when separately bounded |
| Decision | A recorded choice by an authorized person | A comment that mentions the person; a task only for substantive separate human work |
| Verification | Evidence comparing a result with an accepted contract | Part of the producing task, or a separate task when separate review or coordination requires it |

A small fix expresses outcome, implementation and verification in one task. Do not create one item per row. A decision role grants no decision authority; a verification role grants no acceptance authority. Epic/story/task can be used as display names (outcome group, user behaviour, execution) but are not fixed levels. An artifact is the produced document or commit; the task records the work and its acceptance.

## Group and executable

- A **group** is a task that has subtasks; nothing else marks it. It tracks its own outcome and acceptance, cannot be taken, and blocks nothing. Its description names the outcome, accepted scope and how contributions will be assessed.
- An **executable** item gives one current worker a bounded result.
- Do not make one record both a group and a competing implementation assignment. To split an executable item, reconcile its assignment first. If a group needs hands-on integration or acceptance work, express that as an executable task with its own result.

## Three relationships

| Meaning | Direction and question | Effect |
|---|---|---|
| Containment (`parentId`, `task_move`) | child under parent: which outcome does this help achieve? | none by itself |
| Prerequisite (`dependsOn`, `task_dependency`) | consumer depends on producer: what exact result must exist first? | the consumer cannot be taken until it is done or canceled |
| Context reference | work points to a spec, decision, artifact or task: what explains or proves this? | none |

Use one canonical parent; other outcomes reference the work rather than copy it. Every prerequisite names the producer's required result. "Related to", sibling order, a shared parent, an actor label or availability is not a prerequisite. Multiple prerequisites mean all must be satisfied. Keep conditional or mutually exclusive future branches as proposals until a recorded decision chooses one.

No self-dependencies or cycles; do not make a child wait for its aggregate ancestor (the ancestor needs the child's contribution). A producer's status alone does not prove its output satisfies the consumer; a canceled producer supplies nothing, so the consumer's contract is re-evaluated, not assumed met. Siblings without an edge are unordered, which does not prove they can safely edit the same workspace at once.

## Keep one item or split

| Keep one when | Split when |
|---|---|
| One worker can produce a coherent result with clear scope and checks | Distinct outputs need separate expertise, authority, review or handoff |
| Steps are implementation details | One output is a real prerequisite that can be supplied and verified separately |
| A small fix has established behaviour | Uncertainty needs a bounded investigation before implementation can be specified |
| Verification belongs to the same result under current policy | A separate reviewer needs a distinct assignment or evidence |
| The idea is still an undeveloped capture | The next slice is understood well enough to define executable work |

Prefer slices that integrate enough of the system to demonstrate useful behaviour. Frontend/backend/database boundaries justify separate assignments only for a real coordination need; state the integration result and who produces and verifies it. No maximum number of children, fixed depth, estimate or universal duration. Avoid a one-child group unless it preserves a necessary longer-lived outcome.

## Splitting or revising existing work

Read the current contract and version, assignment, decisions, artifacts and actual dependencies first. Record why, and map accepted criteria to the new boundaries. Before another worker starts overlapping work, the current executor hands off and calls `task_release`; the other takes it with `task_assign`. Editing a description or reparenting does not end an assignment. Decide explicitly whether the original stays executable, becomes a group, or is superseded; do not mark it done because children exist. Review each prerequisite against the output it needs: keep it on the original outcome if that is still the required result, or move it deliberately and record why. A restructuring of several edits is not atomic as a whole; record the proposal and coordinate before resuming affected workers. Adding a prerequisite to a held task keeps its holder but blocks anyone else from taking it; adding subtasks to a held task keeps the holder but makes it a group nobody else can take.

## Accepting a group's result

The group owns the criteria for the outcome. Before closing it:

1. Check its accepted scope, contract revision, required contributions and unresolved blockers.
2. Inspect the integrated result against the group's criteria, including failure and permission behaviour. A list of completed tasks is not that demonstration.
3. Record unresolved failures, exclusions or missing evidence honestly. Optional or abandoned work needs an authorized scope disposition; cancellation is not delivery. A failed required child leaves the outcome unsatisfied unless an authorized decision replaces it.
4. Obtain the acceptance current policy requires (accountable person or explicit delegate).
5. State release and product-validation status accurately.

If an accepted result later has changed requirements, preserve its historical acceptance and create or revise work under a new agreement. No percentage of closed children is an acceptance rule.

See [worked structures](../examples/work-structure.md).
