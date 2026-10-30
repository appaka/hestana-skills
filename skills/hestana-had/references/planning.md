# Planning: brief, plan, review, revision

Work at the depth requested. Brainstorming stays in the conversation. A brief is not a plan; a plan is not tasks; backlog tasks are not offered work. Do not climb a level the user did not ask for. A brief lives in your reply until the user asks for a Hestana record.

## Clarifying

Start from what was asked. For a feature establish who is affected and the problem, the observable improvement, constraints and exclusions, and how acceptance would be judged, only as far as they matter; explore failure, recovery and access behaviour when it changes the outcome. Ask **one focused question at a time**: the unknown that most changes the next decision, with context and a recommendation or options. Show only that question. Use the client's structured question UI if it has one and stop while it is pending; otherwise ask one clear question in the conversation. A timeout or missing UI never supplies an answer. In Hestana keep at most one pending question per planning thread.

Give each material question a short local id and keep its answer with who gave it. For each: the question, affected work, the authorized decision-maker if known, status, and the answer with provenance. If you do not know who decides, ask the accountable person whom to ask; never appoint a decider. Hypotheses do not become requirements by repetition. A question blocks only the work that depends on it; independent authorized work continues. A known small fix may need no question; an investigation needs its question, boundary and stop condition. If the user already gave them, put any proposed definition in the description marked proposed instead of asking.

## The brief

Keep (use the [feature brief](../templates/feature-brief.md)):

| Keep | Why |
|---|---|
| Original need in the requester's words, and your interpretation marked as yours | A later reader can tell asked from inferred |
| Who is affected and the observable improvement | The outcome, not the implementation |
| Boundaries: included, excluded, constraints; whether implementation or release is in scope | No scope creep either way |
| Known inputs with references: specs, decisions, related tasks, earlier tries | Reuse |
| Facts, assumptions, decisions, open questions apart; each question with id, effect and who answers | Uncertainty stays visible |
| Acceptance criteria, each marked proposed or accepted (and by whom) | A suggestion is not an agreement |
| How the outcome will be checked | No invented completed checks |
| What can proceed, what waits on which question, one next step | The next reader's start |

Reuse the canonical brief instead of starting a duplicate. A research question needs the question, permitted evidence and a stop condition; an inconclusive result can satisfy it without approving any implementation.

## The plan

Start from the current agreement: brief, accepted decisions, existing work. Plan the next understood slice; speculative later work stays proposed. Use the smallest structure that keeps distinct outputs, authority and checks apart ([work structure](work-structure.md)). For each unit keep: a stable local id and purpose; the result, boundaries and governing brief version; inputs (producing unit and exact output, or pending question); accountable owner and proposed availability (the accountable person sets it); criteria (proposed or accepted) as the task's checklist, with how each is checked; relationships kept distinct; state (proposed, saved with task id and status code, offered). Map each material criterion to the units that produce and check it, including how the group is checked as a whole. Record coverage gaps instead of inventing acceptance. Do not prefill test results, reviewers, approvals or acceptance, and do not name a worker whose fitness and permission are not established.

## Plan quality, against the next activity

Review for a specific next activity (a decision, an investigation, implementation, checking, offering), not "ready" in the abstract. A plan can be ready for a decision while implementation stays blocked. Limit claims to what you read; unread inputs are unverified, not absent. Scale the review: a one-unit fix gets a few sentences.

| Dimension | A finding when |
|---|---|
| Coverage | a criterion has no unit, units are only steps, or closing children is treated as accepting the parent |
| Inputs and uncertainty | an input is missing, a hypothesis is treated as supplied, or a question blocks work it does not affect |
| Relationships | a prerequisite is really an ordering preference, a reference is ambiguous, or canceled work is treated as supplying an input |
| Ownership and authority | a label is treated as permission, or the plan appoints an owner, reviewer or approver nobody authorised |
| Protected operations | the approval boundary is hidden, or offering a task is treated as approval to deploy |
| Evidence | a planned test is reported as passed, or old evidence is reused for a changed scope |
| Recoverability | another reader cannot resume from the records alone, or a partial save is hidden |

For each material finding: criterion or unit, source read, status (passed, gap, unverified, not applicable), activity affected, smallest repair or input needed. Separate a flaw in the plan from a missing product decision or a later implementation obligation. Do not create a task for every finding. Conclude with what can proceed, what is blocked and why, accepted versus proposed, whether tasks were proposed, saved or offered, and one next step. Passing this review does not make the plan executable; offering by the accountable person (or within their delegation) does.

## Saving and handing off

Save only when asked. Save a plan document first, with a stable local id per unit, so a partial save can be resumed rather than repeated; without a plan document the task description carries the brief's essentials and says no plan was saved. Save each unit as a backlog task (mechanics: [Hestana mechanics](hestana-mechanics.md)); record the task id against its local id. Show the accountable person what was saved and what each unit depends on. Offer only on their explicit word or a written delegation you have read and cite; a delegation given only in conversation is first written into the task description or a decision note. If they are not in the conversation, ask with a mention on the parent task (the unit itself if none) and offer nothing until they answer.

## Revising an existing plan

A new chat or agent is not a new feature: continue the existing agreement and task identities. Find the canonical plan by path or id, not title; read the plan, brief, accepted decisions, the unit-to-task mapping, and the status code, owner, assignment and latest handoff of each relevant task. Current records override a cached reply. If something is unreadable keep the reference and report the gap.

| Situation | Do |
|---|---|
| Same scope, nothing new | Reuse; report the next step; no new tasks, no no-op write |
| Clarification within accepted scope | Record it and its effect; do not reopen settled choices |
| Unaccepted change of scope, criteria, priority or method | Keep as a proposed amendment; ask the one consequential question of the person who decides |
| Accepted change of scope | Record who accepted exactly what; keep the earlier contract and evidence; list what to redo or re-check |
| New separable result | Check coverage, add a proposed unit; save as a task only when asked |
| Changed, finished, active or unreadable unit | Reconcile with its current state; do not replace, reopen or reparent as a shortcut |

Write an amendment, not a rewrite: keep the old contract, criteria, task ids, evidence and completion; add the change, who asked, whether accepted, and an impact table (criteria, existing work with ids and status codes, inputs and consumers, evidence that stays valid versus needs a fresh check, authority and next action). Never erase a failed check or a historical completion, carry an old passing review over to a changed candidate, or mark superseded work successful. Do not rewrite the contract of a task someone holds; record the amendment and ask the accountable person how to apply it. A change of the method's version is itself a change: name it and what it requires re-checking.
