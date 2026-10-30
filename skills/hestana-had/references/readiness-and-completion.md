# Readiness, acceptance and completion

Separate meanings; none of them is a new lifecycle or status.

| Concept | Question | What does not establish it |
|---|---|---|
| Readiness for the next activity | Is there enough context, authorization and input for this bounded step? | Filling a form, knowing the whole solution, an open status |
| Acceptance criteria | What observable result did this item promise? | A list of implementation steps, or another item's success |
| Definition of Done | Which applicable quality conditions must this kind of result meet? | A code checklist pasted onto every kind of work |
| Verification evidence | What was checked, against which artifact and contract, by whom, with what outcome? | A plan to check, a self-reported "works", a command that returned without an assertion |
| Acceptance | Has the applicable decision or review process accepted this scoped result? | A comment from someone without that authority, or an answer to another question |
| Release and product validation | Is it available in the intended environment and does it achieve the promised outcome? | Local checks, or a deployment request queued |

Evidence lives in the task `result` and comments, bound to the contract revision it checked. Evidence is neither acceptance nor release. Hestana does not mark evidence stale when requirements change: record the check again against the new requirements.

## Readiness is proportional and activity specific

Capture may remain a title; no gate applies to remembering an idea. A backlog task cannot be taken and becomes executable only when deliberately published.

| Activity | Sufficient preparation |
|---|---|
| Discovery | A question or problem, permitted context, the next useful uncertainty |
| Investigation | A bounded question, evidence scope, authorized inputs, an explicit stop condition |
| Implementation or artifact | A bounded intended result, accepted requirements and exclusions, available inputs, observable acceptance direction, applicable quality and authorization references, no unresolved decision blocking that action |
| Review or verification | An identified candidate revision, governing acceptance and policy revisions, an evidence route, known limits, a reviewer eligible under current policy |
| Release or live validation | The specifically authorized scope and all operational prerequisites |

An unanswered decision stops only the work that depends on it; discovery can be ready while implementation is not. Readiness is not availability or a reservation: the executor also needs current permission, satisfied prerequisites and an assignment whose `until` has not passed. New blockers or changed instructions need a fresh check.

## Writing acceptance

Use a concrete context, action or event, and observable result (Given/When/Then is optional). Prefer visible behaviour or an externally consumable artifact over "works correctly". Include relevant failure, recovery and permission behaviour for the actual work; unresolved expectations are decisions blocking the affected work, not things you invent. A criterion is satisfied only by relevant evidence for the agreed version. A research task that promised a bounded report can finish with a justified negative or inconclusive one; if it promised proof of a capability and the proof is unavailable, the criterion is unverified or failed, and an expired timebox cannot manufacture success.

## Scoped Definition of Done

A result claimed complete meets the item's accepted criteria, the applicable quality and review obligations, required authorization and acceptance, and a recoverable result and handoff.

| Work profile | Quality source and evidence to keep |
|---|---|
| Repository change, including a tiny fix | The repository's own instructions (AGENTS.md or equivalent) and what they point to: required specs and decision records, approvals, code/test/build/security/review/integration checks as actually required. Record their references and exact candidate and outcomes. A small diff waives nothing; do not keep a second copied command list |
| Information-only research or documentation | Agreed question and scope, traceable sources and observations, inference kept apart, honest limits, applicable content review. No code harness merely because a task exists; any repository change or experiment triggers its own rules |
| Human information or decision response | Matches the specific question, from an authorized responder, recorded with provenance. Resolves neither separate human work nor other blockers |
| Separately assigned review | Against the named candidate and contract; findings with scope, evidence and an explicit disposition. Completing it does not accept or release the producer's work |
| Release or live validation | Operational policy, explicit environment and outcome scope, actual environment evidence and observed behaviour. A queued deploy, local build or flag alone is insufficient to claim live usability |

Select profiles by actual actions and outputs, not labels. Unknown policy, review route or acceptance authority stays explicit; continue only independently authorized actions and resolve the uncertainty before claiming the affected result complete.

## Evidence at completion

For each material criterion or quality obligation make recoverable: the contract revision (and this skill's version); the exact candidate (commit, artifact, revision) and environment or fixture; the check performed, observation and limitation; who checked and when, plus the review and acceptance disposition required; any unanswered question, failed or unverified obligation, and the release or validation step. Use plain outcomes: passed, failed, unverified, not applicable (only where a conditional check's trigger truly does not apply). Planned checks remain plans until observed. Keep it proportionate: a short report can carry several facts. Do not copy secrets or private material; use an authorized reference. If a required verifier cannot see enough, record the gap; do not declare success or change access yourself. A tool failure can explain an unverified result; it cannot make a criterion pass. Exceptions need real authority, a specific scope and a recorded rationale.

## Review, correction and parent acceptance

The producer verifies, then obtains whatever review and acceptance current rules require. Do not invent a reviewer assignment where none is required; do not self-approve where a separate reviewer is required. Record feedback against the candidate and criterion; correct, and repeat the affected checks plus any full gate the governing workflow requires. A pass on an earlier candidate is not the corrected candidate's evidence. A review task can finish with an honest rejection; the producer is not thereby accepted. For a group, apply [parent acceptance](work-structure.md).

## Completion and release claims

If the contract promises a reviewed candidate and excludes deployment, it can finish when that promise and the quality obligations are met; the result says "not released". Required integration checks still apply. If it promises the feature to real users, deployment and the specified user-visible checks are part of the promise and the outcome stays unsatisfied until they hold. A measured improvement needs the agreed observation. Do not silently narrow a live-outcome task to implementation to close it; a scope change needs authorized agreement, preserved history and treatment of the remainder.

## Versions and revalidation

When scope, decisions, inputs, the candidate or applicable policy changes, map the change to affected criteria and evidence and re-run affected checks and the broader gates required. Preserve earlier accepted results and evidence; a changed requirement may create new work without falsifying an accurate historical result. Mandatory security and project rules still apply regardless of the method.

Examples: [completion](../examples/completion.md).
