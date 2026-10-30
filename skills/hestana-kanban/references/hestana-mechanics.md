# Hestana mechanics for Kanban

Use the schemas you actually have; never call a tool or pass an argument because another surface has it. The agent surface uses `task_*`, `files_*`, `notes_*` and `spaces_*`; the person surface uses `tasks_*` operations (found with `operations_search`, run with `operation_run`) and follows the same model. Make every `idempotencyKey` unique to its write (include the task id or local id); reuse a key only to retry the same write after an uncertain reply.

## Space and methodology
- `spaces_get` returns the Space and `methodology: { id, version, skill, summary } | null`; `spaces_list` returns it without `summary`. No tool writes it for agents: only the Space owner chooses, in the interface.
- `spaces_members` gives user ids for mentions and owners.

## Statuses
Each Space names its statuses over six fixed states (backlog, open, doing, waiting, done, canceled). `task_statuses_list` (person: `tasks_statuses_list`) gives each `code`, label and state. Pass a `code` to `task_create` (`status`) and `task_set_status`; never a label, a state name, a row id, or a code from an example or another Space.

## Reading
`task_list` / `task_get` (`availability`, `ownerUserId`, `status`, `headVersion`, `blockedBy`), `task_next` (suggests takeable work, reserves nothing; eligible = open state, no effective assignment, no unfinished prerequisites, no subtasks, availability that allows you; `null` = nothing now), `task_context` (only `taskId`; page a section with `section` and `cursor`), `notes_list` (comments; `after` a comment id). Documents: `files_list`, `files_read`, `objects_get`.

## Availability and owner
`ownerUserId` is the accountable person, always a person, independent of who works. `availability`: `HUMAN` persons only, `ACTOR` agent identities only, `ANY`. A disallowed call is refused with nothing written: report it. Only a person widens availability.

## Assign
`task_assign` with `taskId`; omit `assignee` for yourself; `until` is a future ISO instant (an ACTOR must give it; renew with a later one). An expired reservation reads as free. There is no assignment token: after a gap read the task again before releasing or continuing. `replace: true` replaces another holder; only if a person told you to. `task_assign` also hands work to a named principal (`assignee: {type, id}`); closed tasks cannot be assigned. Assignment is coordination, not a lock and not permission to write. Taking never changes the status.

## Comments
`notes_add` on the task with text and optional `label` (`decision`, `progress`, `handoff`), `pinned`, `replyTo`, `mentions`. `noteType` has no effect. Comments need no assignment, so you can hand off after losing yours. To ask: `mentions: [{ userId, awaitsAnswer: true }]` and one self-contained question; it stays pending until that person replies or dismisses it; you may withdraw it.

## Status, result, release
`task_set_status` takes the status `code`, optional `result`, and `expectedVersion` as last observed (planning offers also pass `expectedStatus`). Closing (done or canceled) clears the assignment; a `result` moves `headVersion`. It takes no idempotency key: after an uncertain reply read back with `task_get` first. `task_release` (`taskId`) clears the assignment and changes neither state nor status. Any writer can release, change owner or availability, so do not for a card you do not hold unless a person asks.

## Creating and structure
`task_create` (`status`, `ownerUserId`, `availability`, `priority` 0-9, `checklist`, Markdown description, `parentId`, `dependsOn`, `idempotencyKey`). Omitting `status` lands in the open default. `task_update` (full description plus link) and `task_move` (`taskId`, `parentId`) change an existing card; editing the description moves `headVersion`, so re-read and revalidate after a conflict. `task_dependency` (`spaceId`, `taskId`, `prerequisiteId`, `action: 'add'`); the server refuses cycles. Unfinished prerequisites never change a status: they show as `blockedBy` and block taking, not closing.

## Documents
`files_create` (stable path, `typeKey: note`, `whenToUse`, `idempotencyKey`) and `files_write` (`expectedVersion` = the `headVersion` you observed; on conflict re-read and merge; after two failed tries stop and report). Link a document deliverable from the card description before sending it to Review.

## Checking
There is no server verification step. Write each check, outcome and evidence in the `result` or a comment, failures included.
