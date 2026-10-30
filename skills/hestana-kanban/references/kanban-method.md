# Kanban method (0.1.0)

Source text: the Kanban 0.1.0 package, rewritten as a skill. Kanban adds conventions inside Hestana's task model. It changes no permission, creates no server rule and does not enforce the work-in-progress limit.

## The board

Seven statuses over Hestana's six fixed states (backlog, open, doing, waiting, done, canceled). The Space owns labels and codes; read them with `task_statuses_list`.

| Column | State | Notes |
| --- | --- | --- |
| Backlog | backlog | Cannot be taken. |
| To do | open | The only column `task_next` offers from. |
| In progress | doing | Someone is working on it. |
| Review | waiting | Finished, waits for the owner to accept. Added by the methodology; not a default status of its state. |
| Waiting | waiting | Stopped on something outside. The default status of the waiting state. |
| Done / Canceled | done / canceled | Closing clears the assignment. A task stopped for good is canceled, not left in a column. |

Review and Waiting share a state, so they are told apart by their code and by meaning: Review = "a person must accept this"; Waiting = "blocked on an answer or a third party". If the Space has other codes, map them to the states and keep one default per state; do not create parallel columns.

## Principles in operation

- **Pull, not push.** Nobody assigns work onto another worker. A worker takes a card when there is capacity. Reading the suggested next task reserves nothing.
- **Explicit policies.** What "ready" means (To do), what "finished" means (the card's description), who accepts (the owner) and the work-in-progress limit are written down in the Space, not assumed. If a policy you need is not written, ask; do not invent it.
- **Limit work in progress.** The Space owner declares the limit (for example "In progress: N", or "each person holds at most N cards in In progress"). Hestana holds no limit and will not stop anyone. Before pulling, count the cards in the column or held by you. At the limit, finish or unblock instead; say so in a comment on the oldest card in that column and help it forward. No limit declared: ask the owner for one; do not invent a number.
- **Finish before you start.** Prefer moving a Review card to Done (when it is yours to move) or unblocking a Waiting one over pulling.
- **Expedite is an exception, not a column.** The owner raises priority; say in a comment why a card jumped. The limit still holds unless the Space says otherwise.
- **Review the board each session.** Stale In progress cards (deadline passed, no recent note): release or re-plan only your own; for another worker's card, comment and mention the holder or the owner, and change nothing unless a person told you to.

## A card

A card is a task. Three separate questions: the **owner** (`ownerUserId`, a person, accountable whoever works), the **availability** (`HUMAN`, `ACTOR`, `ANY`: who may take it) and the **assignee** (who holds it now, with an `until`). Minimum for a pullable card: a title naming a result, a description saying what finished means, a priority 0-9.

A task with subtasks is an aggregate: it cannot be taken; work through the subtasks; the owner closes the aggregate explicitly.

## Not covered

Estimates, sprints, roles, a quality policy. For code, the repository's own specification, testing, review and delivery requirements still apply. Kanban authorises nothing: system rules, access and project policy govern.
