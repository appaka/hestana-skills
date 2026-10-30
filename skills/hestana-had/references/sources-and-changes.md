# Sources and changes

This skill is a rewrite of the package human-agent-development 0.7.0 (format 1) as an installable skill. The method is unchanged. What changed is the carrier: the package was read from a Space and applied through an adoption record and a binding that pinned file versions; the skill travels with the agent, reads only the Space's methodology setting from `spaces_get`, and never blocks.

## What Hestana provides for this method (the names are those of the MCP server)

| Need | Behaviour |
|---|---|
| Capture without dispatch, deliberate publication | Backlog status, later moved to an open one; backlog work is not offered (`task_create`, `task_set_status`) |
| Prerequisites | One at a time, cycle-safe; unfinished prerequisites block taking (`task_dependency`, `dependsOn`) |
| Owner and who may execute | `ownerUserId` (a person) and `availability`; a task with subtasks is a group and cannot be taken |
| Taking and giving up work | `task_assign` with an optional deadline (required for an ACTOR), `task_release`, `task_next`; expired reservations are free; closing clears the assignment |
| Questions to a person | A comment that mentions the person and awaits an answer; it does not pause the task |
| Approval of a governed action | No approval parking of tasks; a question to the accountable person or a rule of the project or repository |
| Recovering context | `task_context` |
| Verification evidence | In the task `result` and comments; no record of its own |

## Source rationale (from the package, read 2026-10-15)

The workflow is an original synthesis, not compliance with Scrum or another framework. It draws on: GOV.UK Service Manual on discovery (understand the problem before a solution; allow a decision not to proceed); Scrum Guide 2020 on backlog refinement and Definition of Done (acceptance, quality policy and evidence kept separate; no Scrum events or roles adopted); GitHub coding-agent task guidance (bounded tasks, acceptance, code context); Shape Up on scope mapping and getting one piece done (integrated slices, no cycles adopted); Cucumber Gherkin reference (context, action, observable result as an optional writing aid); Agile Manifesto principles (frequent useful delivery, proportional evidence).

## History

- 0.7.0 aligned the package with the task model v1: owner, availability and assigned principal; `task_assign` and `task_release`; questions as mentions; evidence in result and comments; no approval parking.
- 0.6.0 removed capability profiles, delegated answers, alert escalation and independent verification checks.
- Earlier versions: see the package's verification records in the publishing Space.
- This skill 0.7.0: first release as a skill; adds Space binding (`spaces_get`) and the never-block rule; drops the adoption record, binding and per-file version pinning.
