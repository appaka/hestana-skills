# Hestana mechanics used by this skill

Use only the tools and arguments you actually have; do not call one because another surface has it. Every `idempotencyKey` must be unique to its write (include the task id); reuse a key only to retry the same write after an uncertain reply.

**Methodology.** `spaces_get` returns `methodology: {id, version, skill, summary} | null`; `spaces_list` returns it without `summary`. Nothing in the server checks which skills you have.

**Statuses.** Each Space names its statuses (code, label, state) over six fixed states: backlog, open, doing, waiting, done, canceled. `task_statuses_list` returns them; pass a status `code`. Person surface equivalents are `tasks_*` operations found with `operations_search` and run with `operation_run`.

**Reading.** Compact lists first (`task_list`, `files_list`), then `task_get` (`headVersion`, `status`, `availability`, `ownerUserId`, `blockedBy`) or `files_read` for strong matches.

**Creating.** `task_create` with `status` (a backlog code for the Inbox), optional `ownerUserId` (a person; defaults to the person you act for), `availability`, `parentId`, `dependsOn`, `priority`, `checklist`, description (Markdown) and `idempotencyKey`. Omitting `status` uses the open default and offers the task. Descriptions are Markdown: a blank line between paragraphs.

**Structure.** `task_move` (`taskId`, `parentId`) places a task under a parent; a task with subtasks is a group and cannot be taken. `task_dependency` (`spaceId`, `taskId`, `prerequisiteId`, `action: 'add'`) adds a prerequisite; cycles are refused. A prerequisite never moves a status; `blockedBy` says what is open. Closing a blocked task or a group is allowed; only taking is blocked.

**Availability.** `HUMAN`, `ACTOR` or `ANY`; the Space's settings give the default. It grants no permission and names no worker. Only a person widens it.

**Select / assign.** `task_next` suggests; `task_assign` with `taskId`, no assignee for yourself, `until` a future ISO instant (required for an ACTOR); renew by assigning again with a later `until`. An expired reservation reads as free. There is no assignment token: read the task again after any gap before releasing or continuing. `task_release` clears the assignment and changes no status.

**Status moves.** `task_set_status` with the status `code`, `expectedVersion`, and `result` when closing. Closing (done or canceled) clears the assignment. It takes no idempotency key: after an uncertain reply, `task_get` before retrying. A refusal wrote nothing.

**Comments.** `notes_add` on the task, optional `label` (`decision`, `progress`, `handoff`), `replyTo`, `pinned`. To ask a person: `mentions: [{ userId, awaitsAnswer: true }]` with ids from `spaces_members`, one self-contained question. It notifies, stays pending until answered or dismissed, and changes neither status nor assignment. Read answers with `notes_list` (`after` your comment's id). Only the asked person answers. `noteType` has no effect.

**Editing.** `task_update` takes the full description; editing moves `headVersion`, so re-read after a conflict.

**Documents.** `files_create` / `files_write` (`expectedVersion`), read with `files_read`.

**Checking.** There is no server verification step. Write what you checked, the outcome and evidence (commit, document and version, URL) in the closing `result` or a comment, failures included.
