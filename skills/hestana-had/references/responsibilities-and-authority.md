# Responsibilities and authority

Separate: the person accountable for the project, the participant proposing work, the executor, the principal the task is assigned to, and the authority for a particular decision. Actual permissions and, where one exists, a recorded delegation decide what anyone may do; a runtime name ("Claude Code", "Codex") or a self-description decides nothing.

## Defaults (AUTH1-AUTH6)

| Ref | Responsibility | Default | Boundary |
|---|---|---|---|
| AUTH1 | Planning participation | Members with access, people or agents, may propose, ask and refine | Within their permitted reads and writes; no automatic disclosure of private chats; cannot bypass a denied write |
| AUTH2 | Project accountability and product decisions | One accountable person owns outcome, scope and priority and may delegate a bounded product decision | Delegating does not remove accountability, grant access or approve protected actions; technical discretion inside accepted scope stays with the executor |
| AUTH3 | Planner publication | A planner may publish (backlog to open) prepared tasks within accepted scope under an explicit bounded delegation | No delegation means capture and proposal only; a planner cannot decide new scope or widen its own delegation |
| AUTH4 | Execution requirements | The task's owner decides who may take it: `HUMAN`, `ACTOR` or `ANY` | Anyone with write access may change availability or owner; a change that contradicts the current holder is refused until the task is released or reassigned. Availability grants no permission |
| AUTH5 | Asking a person | A comment that mentions the person and awaits an answer; only that person answers, as themselves | If you do not know whom to ask, ask the accountable person whom to ask; that does not make them the answerer. No timers or escalation are invented |
| AUTH6 | Completion and acceptance | The executor may close a technical task when criteria, evidence and required review are met; the accountable person or an explicit delegate accepts a feature outcome | No bypass of quality policies, protected approvals or release rules; no human approval is required for every technical task merely because it is a task |

The accountable person is a role: the task's `ownerUserId` for a task, and for the project the person the Space's work is accountable to (the person you act for unless the task, brief or a written record names someone else). Do not appoint one. Owner, accountable person and assigned principal are separate things. Being named in a plan does not impersonate a person or widen membership.

Suitability is the executor's own judgement within the task's availability and the work's needs. The method has no capability catalogue: describe required expertise in the task, and decline or hand back work you cannot do well.

## Explicit bounded delegation

The accountable person may delegate a bounded product decision (AUTH2) or publication (AUTH3) to a person or an agent. Hestana has no delegation record; write it where it is directly retrievable (brief, task description, or a decision note). It needs: grantor, grantee, permitted decision or action, project or feature scope, limits and conditions, and when it was given. Add an expiry only if actually granted; assume no right to redelegate.

A delegation given only in conversation must first be written down before you act on it. Before dependent action, read the delegation and the current contract. Expired, revoked, conflicting, out-of-scope or unreadable authority cannot justify the action. A planner cannot grant, extend or reinterpret its own delegation. A delegation records who decides; it is not a permission, approves no protected action, and lets nobody answer a question addressed to someone else.

## Publication by the planner

Publish only when a delegation you have read covers the unit, it stays inside accepted scope, and the unit is prepared (see [readiness](readiness-and-completion.md)). It may refine implementation detail and decomposition inside that outcome, preserving accepted decisions, parent versus prerequisite meaning, revisions and any current reservation. New scope, changed acceptance, protected actions and release still need their own decision. Never publish merely because a plausible template exists.

## Human assistance

Distinguish three needs: information or a product choice (a mention that awaits an answer), approval for a governed action (the approval mechanism of that action or a question to the accountable person; Hestana has no approval parking of tasks), and human-produced work (a separate task with a deliverable and a prerequisite). A reply is not evidence that separate human work is done, and a comment is not an approval. If an explicit human response is required, an agent cannot replace it; it may supply evidence for the person to decide. Details: [interruption and handoff](interruption-and-handoff.md).

## Verification, review and acceptance

Evidence in the result and comments is evidence, not approval. Hestana does not require the verifier to differ from the executor; when repository or project rules require review by someone else, follow them and record who reviewed. A review can reject a result, and a passing review supplies no unrelated release authority. Closing a task, accepting a feature and releasing it are distinct authorized actions; record the actual actor, contract or candidate, evidence and delegation reference. Release operations keep their own approval rules.

What the server itself provides is described in [Hestana mechanics](hestana-mechanics.md) (availability, assignment, blocking by prerequisites and subtasks, an owner who is a person). It does not route work by capability, let anyone answer for another person, retry or escalate alerts, require a verifier to differ from the executor, or accept a feature outcome. Where the method needs one of these, it is a human decision recorded in the work; never present a convention as an infrastructure guarantee.

Examples: [authority](../examples/authority.md).
