# Planning under Kanban

Planning ends where pulling begins: you save cards in the backlog, the owner makes them ready (To do), and workers pull them.

## Levels

Work at the depth asked. A brief is not a plan; a plan is not cards; backlog cards are not offered work. Keep brainstorming in the conversation. Save only when asked.

## Read before asking

Look for related briefs, decisions and cards: `files_list`, `task_list` (compact), then read strong matches (`files_read`, `task_get`). Keep facts (with source), assumptions, decisions (who decided) and open questions apart. Ask **one** consequential question at a time, with context and a recommendation; do not supply an answer a person has not given. If you do not know who decides, ask the owner; never appoint a decider.

## What a card needs

- **Title:** a result ("Checkout shows the VAT line"), not an activity ("Work on checkout").
- **Description (Markdown, blank line between paragraphs):** what finished means in observable terms; inputs and links; what is out of scope; how it will be checked (the plan to check is text; evidence goes later in `result` and comments); a link to the plan or brief if one exists.
- **Priority** 0-9; higher is pulled first.
- **Availability:** leave the Space default unless the work needs it. `ANY` only when an agent could really do it. The owner sets or approves it; you propose.
- **Checklist** (optional): observable outcomes; steps that help the worker. They do not replace the description.
- **Size:** one card, one result. Split only when a card would produce a different result, need a different person, need another card's output, or need its own review. Not by layer, not to fill a hierarchy.

## Saving

1. Read `task_statuses_list`; take the backlog `code`.
2. `task_create` with `status` = that backlog code, `ownerUserId` (a person; defaults to the person you act for; name another only if told), `priority`, `checklist`, description, `parentId` if the parent exists, and an `idempotencyKey` unique per card (include a stable local id; retry only with the same key and identical arguments).
3. Before creating, page `task_list` and read strong matches: different wording is not a different request. If a card exists, reuse it, create no second one, leave its contract and status alone.
4. Prerequisites only where a card needs another's output: `dependsOn` on create or `task_dependency` (`spaceId`, `taskId`, `prerequisiteId`, `action: 'add'`). A prerequisite does not move the status; it shows as `blockedBy` and the card cannot be taken until the prerequisite is done or canceled. Groups (`parentId`, `task_move`) mean "contributes to this outcome" and block nothing; sibling order is not a prerequisite.
5. Read each card back with `task_get` and report its `headVersion`, `status`, `availability`, `ownerUserId`, `blockedBy`.

## Making cards ready

Move a card from Backlog to To do (`task_set_status` with the To do code, `expectedVersion` and `expectedStatus` as just read) **only** when the owner explicitly asks you to, or when a written, bounded delegation from them that you can read covers that card (cite it). A delegation given only in conversation must be written down first (grantor, grantee, permitted action, scope, limits, date) on the card or a decision note. Otherwise ask the owner with a comment that mentions them and awaits an answer on the parent card (the card itself if none), and offer nothing until they reply. Respect the declared work-in-progress limit when recommending how many cards to make ready, but do not set one. A refused move is an answer: report it.

## Report

What was saved (ids, status codes, versions), the methodology and version read, accepted versus proposed, open questions and who answers them, and the single next step. Saved backlog cards are neither offered, implemented, accepted nor released; say which of these actually happened.

## Revising

Continue the existing cards and ids; a new chat is not a new feature. Do not rewrite the description of a card someone currently holds: record the change in a comment and ask the owner how to apply it. Never erase a failed check or a historical completion. Adding subtasks under a held card keeps the holder but makes it a group nobody else can take; say so.
