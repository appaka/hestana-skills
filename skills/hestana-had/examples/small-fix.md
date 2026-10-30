# Small fix walkthrough

Illustrative scenario: an existing task-list empty state repeats its heading because the same label is rendered twice. The expected single heading is already established by the accepted design. Fictional; no task is created.

## One useful task

Capture starts with "Remove the duplicate empty-state heading." Before execution, enrich that same item:

- Problem and evidence: the empty list renders the accepted heading twice; link a reproduction or screenshot.
- Intended result: the empty list displays the existing heading once and keeps the existing action.
- Boundary: correct the duplicate rendering; no wording, permission, query or redesign change.
- Inputs and checks: accepted design, reproduction, applicable repository rules, a check of empty and non-empty states.

No mandatory epic, story, discovery document or research task. The current request and policy determine whether execution is authorized; an agent does not infer authority from a title.

## Execute and verify

The worker takes the task with `task_assign` and a short `until`, confirms the reproduction and the established expectation, reads the task context and follows the repository's required code workflow. The task keeps its owner; the worker is only the assigned principal. It makes the bounded correction, verifies the affected behaviour, obtains the required review and records the artifact or commit and the check evidence in the task result and comments. One short result and handoff can carry references, verification outcome and any remaining publication step. Closing the task clears the assignment and does not claim production deployment.

## When the path changes

If investigation shows the two headings represent different accessibility roles, the expected behaviour is no longer established. The worker records the uncertainty, asks the appropriate decision-maker with a mention that awaits an answer, holds the affected change, and if nothing else can proceed releases the task with `task_release`. It does not treat a tiny diff as permission to redesign the interface. A fresh worker needs only the task, the linked design and reproduction, the artifact and the check result.
