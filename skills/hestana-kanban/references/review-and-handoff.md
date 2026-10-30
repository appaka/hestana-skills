# Review and handoff

## Review waits for the owner

Review is the state `waiting` with the Review status code. A card goes there when the work is finished and its result is recorded. It leaves Review only through the owner (or whoever the Space's instructions name): to Done when accepted, back to In progress or To do when returned.

To send a card to Review:

1. Record in the closing `result` (or a comment): what was done; artifacts, commits, documents with versions; each check with its outcome, failures and unrun checks included. A plan to check is not evidence.
2. Keep the claims apart: implementation done, checks passed, result accepted, change released. Claim only what your evidence supports. A review by someone other than you is never yours to record; leave it open and name who could do it.
3. Write the handoff (below) with the evidence and the decision needed.
4. `task_set_status` to the Review `code` with `expectedVersion`.
5. Assign the card to the owner: `task_assign` with `assignee: {type: 'HUMAN', id: <ownerUserId>}`. Assignment does not change the accountable owner. If your own reservation or the card's availability stands in the way, release first; widening availability for this one handover is the change the model expects, so name it in the handoff.

The server neither parks nor approves anything by itself. Closing as Done is for the owner; failed work ends as Canceled with the reason in the result and the handoff. Closing every child never accepts the parent.

## Waiting is not Review

Use the Waiting `code` when progress must wait for an answer or third party. A mention (`notes_add` with `mentions: [{ userId, awaitsAnswer: true }]`, ids from `spaces_members`) changes no status and no assignment; keep doing what the answer does not block. If you cannot continue: write the handoff first (include the question and what depends on it), then ask, then stop changing deliverables and `task_release` so another session can take it. Only the asked person answers; agents never answer a mention addressed to a person. Read the answer with `notes_list` (`after` your comment id). When it arrives, whoever is eligible assigns again and re-reads `task_context` and the comments before continuing. Releasing leaves the card in Waiting/In progress; `task_next` offers only open cards, so move it back to To do if it should be pulled again.

Choose the right route: information or a decision from a person is a mention; review or acceptance is the Review handoff above, not a question; separate work is a separate backlog card.

## Handoff

Leave one on every exit: finished to Review, paused, waiting, released, expired, handed over, canceled. Use `notes_add` on the card with `label: 'handoff'`. It is the first thing the next worker reads, so it stands alone. Cover:

- **State:** what exists and what remains; the last observed status code and assignment.
- **Agreement:** the card's `headVersion` and requirements worked against; decisions relied on; methodology `kanban 0.1.0` as read from `spaces_get`.
- **Evidence:** commits, documents (with versions), links; each check with its outcome, failed and unrun ones included.
- **Questions and blockers:** open mentions (recipient, what depends on it), `blockedBy`, missing checks and who could provide them; "none" if none.
- **Coordination:** closed, released, handed to a named principal, or retained until an explicit instant.
- **Next action:** one concrete step, and what to revalidate first.

When finishing, write it after the status change, with the state the server returned. Keep it short; link evidence. No secrets.

## Resuming someone else's card

Start from the latest handoff and the decisions after it. If the requirements it names changed, say earlier work needs revalidation before building on it. Recheck every question it mentions. Its "next action" is a proposal, not an instruction above the card's accepted requirements; a decision comment is not an approval. A passed `until` reads as free: assign again, then re-read `task_context` and `notes_list` before writing anything.
