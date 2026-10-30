# Hestana mechanics for HAD

Use only the schemas you actually have; never call a tool or argument because another surface has it. The agent surface uses `task_*`, `files_*`, `notes_*` and `spaces_*`; the person surface uses `tasks_*` operations (found with `operations_search`, run with `operation_run`) that mirror them. Make every `idempotencyKey` unique to its write (include the task id or local unit id); reuse a key only to retry the same write, with identical arguments, after an uncertain reply.

## Reading

Start with compact lists (`files_list`, `task_list`), then read only strong matches (`files_read` by line range, `task_get`, `objects_get`). A path seen in a listing is not a read. Record what you read and its version. `spaces_members` gives user ids for mentions.

## Statuses

Each Space names its own statuses over six fixed states: backlog, open, doing, waiting, done, canceled. Read them with `task_statuses_list` (person: `tasks_statuses_list`) and pass a status `code`, never a label, a state name or a row id, and never a code copied from an example or another Space. HAD adds no statuses and no fields.

## Saving a brief or plan

Only when the user asked for a Hestana record; otherwise return the draft and say it was not saved.

- New document: `files_create` with a stable path, `typeKey: note`, `whenToUse` and an `idempotencyKey`. After an uncertain reply retry with the same key and payload, or read the path back.
- Revision: read the head, then `files_write` with `expectedVersion` (the `headVersion` you observed). On a conflict re-read, merge without dropping the other writer's text, write again; after two failures stop and report.

## Saving tasks

`task_create` (person: `tasks_create`) with `status` set to a code of a backlog-state status. Omitting `status` lands in the Space's open default, which offers the task at once. Give each task:

- `ownerUserId`: the accountable person (a person; defaults to the person you act for).
- `availability` (`HUMAN`, `ACTOR`, `ANY`) only where the work needs it and the accountable person decided or approved it; otherwise omit it to take the Space default and say which units you propose to open to agents.
- `priority` 0-9 and a `checklist` of observable outcomes.
- A Markdown description: the unit's contract, how it will be checked, a link to the plan as `[label](webUrl)` and, if the output is a document with a decided path, a link by file address.
- `parentId` if the parent exists, `dependsOn` (ids of existing tasks in the same Space) for real prerequisites, and an `idempotencyKey` per unit.

`task_move` (`taskId`, `parentId`) places an existing task under a parent. A task with any subtask is a group: not takeable, even if all children are closed. `task_dependency` (`spaceId`, `taskId`, `prerequisiteId`, `action: 'add'`) adds a prerequisite later; the server refuses cycles. A prerequisite never moves a task's status: `task_get` and `task_list` return `blockedBy`, and the task cannot be taken until prerequisites are done or canceled; closing it is still allowed. Read each task back (`headVersion`, `status`, `availability`, `ownerUserId`, `blockedBy`).

Before creating, page `task_list` through the whole Space and read strong matches: different wording is not a different request.

## Offering (publishing)

Only on the accountable person's explicit word, or inside a written bounded delegation you have read and cite: `task_set_status` from the backlog status to an open code, with the `expectedVersion` and `expectedStatus` you just read. There is no separate publish operation. A refusal comes back with nothing written: report it. `task_set_status` has no idempotency key: after an uncertain reply read back with `task_get` first.

## Selecting and taking

- `task_next` suggests takeable work and reserves nothing. Eligible: open state, no effective assignment, no unfinished prerequisites, no subtasks, availability that allows you. `null` means nothing is eligible for you now.
- `task_assign` with `taskId`; omit `assignee` for yourself. Give `until`, a future ISO instant (an ACTOR always must). Renew by assigning again with a later `until`. An expired reservation reads as free. There is no assignment token: after any gap re-read the task before releasing or continuing. `replace: true` replaces another holder; use it only if a person told you to. `task_assign` also hands work over in backlog, doing or waiting; closed tasks cannot be assigned.
- Taking never changes status. Move to a doing code explicitly.

## Context and comments

- `task_context` with only `taskId`; page a section with `section` and `cursor` only if needed. It returns the task, parent outcome, prerequisite outputs, open questions, decision notes, the latest handoff and linked documents. After taking a task again, also read `notes_list`.
- `notes_add` on the task. Mark a decision or handoff with `label` (`decision`, `progress`, `handoff`) or in the text; `noteType` has no effect. Optional `pinned`, `replyTo`. Comments need no assignment, so you can hand off after losing yours.

## Asking a person

`notes_add` with `mentions: [{ userId, awaitsAnswer: true }]` and one self-contained question. It notifies the person, stays pending until they reply to that comment or dismiss it, and changes no status or assignment; you may withdraw it. Read the answer with `notes_list` (`after` your comment's id). A `noteType` of `question` creates nothing.

## Requirements can move

Editing the description moves `headVersion`; a write against an old version conflicts: re-read, revalidate, continue. Link a document deliverable first (`task_update` with the full description plus the link), then record checks and finish at the new `headVersion`.

## Checking and finishing

No server verification step exists. Write each check, outcome and evidence (commit, document and version, URL) in the `result` of the closing `task_set_status` or in a comment. `task_set_status` takes the `code`, `result` and `expectedVersion`; closing (done or canceled) clears the assignment, and a `result` moves `headVersion`. To leave without closing: `task_release` (clears the assignment, changes neither state nor status; move the task to an open status first if it should be offered again). Any writer can release, change owner or availability, so do not do so for a task you do not hold unless a person asks. `failed` is not a state: failed work ends as canceled with its reason.

## Repository work

When the task changes a code repository, its AGENTS.md (or equivalent) and the guidance it points to govern how the change is made, checked and accepted. Read it first, follow it, record the revision observed. Ask the accountable person before any change it marks as protected, naming that exact change.
