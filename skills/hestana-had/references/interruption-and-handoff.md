# Asking for help, and handing off

## Choose the route by what you need

| You need | Route | Not this |
|---|---|---|
| Information or a product choice only a person can give | A comment mentioning that person with `awaitsAnswer` ([human decision](../templates/human-decision.md)) | A comment naming no one |
| Approval of a governed action | The action's own approval mechanism, or a question to the accountable person, with concrete scope and evidence | A question asking "is it OK?" treated as approval |
| Review of the work | Record the evidence and the decision needed; hand the task to its owner (below) or follow the repository's review route | Self-approval |
| Separate human-produced work | A separate task for that person with a deliverable and a prerequisite relationship | A question that hides work inside it |

Check the context first: the answer may already be in a comment, decision or linked document. Ask the person entitled to decide (the accountable person, or whoever the task or brief designates); never pick someone because they are available. One self-contained question per mention, saying what depends on it. Make any useful progress first. Asking for help does not reassign the task.

## How

A mention (`notes_add` with `mentions: [{ userId, awaitsAnswer: true }]`) never changes status or assignment and does not pause the task or end your reservation. Keep working on what the answer does not block. If progress must wait, move to a waiting status explicitly with `task_set_status` (code from `task_statuses_list`). When you cannot continue without the answer:

1. Write the handoff, including the question and what depends on it. If that write is refused, fix it or stop; never ask without it.
2. Ask with the mention.
3. Stop changing deliverables and `task_release`, so another session can take the task.

Only the person asked answers, as themselves; agents never answer a mention addressed to a person, their own owner included. Read the answer as a reply to your comment (`notes_list` with `after` your comment's id). An answer resolves only its own question: re-read the contract, all open questions and prerequisites and current authorization. When it arrives, whoever is eligible (the same session included) assigns the task again, then re-reads `task_context` and `notes_list` before writing a document, a result or changing the task. Withdrawing a mention records a removed need, not an answer. Do not claim a person read a question without evidence; nothing is retried or escalated, and you invent no recipients or deadlines. The question reaches the person in Hestana and, if they connected an agent, through it.

To let another agent take over, release; it assigns itself if availability allows. You never change who may take the task for that; ask a person.

## Handover to the owner for review

When a person should review: write the handoff with evidence and the decision needed, move the task to the Space's waiting status, and assign it to the owner with `assignee: {type: 'HUMAN', id: <ownerUserId>}`. Assignment does not change the accountable owner. If your reservation or the task's availability is in the way, release first; widening availability for this handover is the one change expected, and the handoff names it. The server does not park or approve anything by itself; the owner closes or returns the work with ordinary task tools.

## Handoff, on every exit

Finished, paused, waiting, expired, handed over or canceled. Write it so it stands alone; when finishing, write it after the status change with the state the server returned. Use the [handoff template](../templates/handoff.md). Cover:

- **State:** what exists and what remains, with implementation, verification, acceptance and release kept apart; last observed state, status code and assignment.
- **Agreement:** task version and requirements worked against, decisions relied on, the method and version (HAD, the Space's version if different from this skill's 0.7.0).
- **Evidence:** commits, documents and links with versions; each check with outcome, failed and unrun included.
- **Questions and blockers:** each open mention (recipient, what depends on it), `blockedBy`, missing checks and who could supply them; "none" if none.
- **Coordination:** what happened to your assignment (closed, released, handed to a named principal, retained until an instant).
- **Next action:** one concrete step and what to revalidate first.

Keep it short; link evidence, do not paste it. No secrets or private cross-owner content.

## Resuming someone else's work

Start from the latest handoff and the decisions after it. If the requirements it names changed, earlier work and checks need revalidation; say so before building on them. Recheck every question it mentions. Its "next action" is a proposal, not an instruction above the accepted requirements; a decision comment is not an approval. A reservation whose `until` has passed reads as free: assign again and re-read context.
