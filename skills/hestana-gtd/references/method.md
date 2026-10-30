# GTD in Hestana terms (package gtd 0.1.0)

A personal way of working: **capture** everything that has your attention, **clarify** what each thing is, **organize** it where it belongs, **review** regularly and **do**. The person decides what each thing means; agents help capture and prepare. These are conventions inside Hestana's task model. They change no permission and create no server rule: the server stores statuses, states, availability, subtasks and prerequisites, and knows nothing about GTD.

## The lists

| List | State | Meaning |
|---|---|---|
| Inbox | backlog (default status) | Captured, not yet clarified. Cannot be taken. |
| Someday/maybe | backlog (second status) | Clarified and deliberately not committed to. Cannot be taken. |
| Next actions | open | The next physical action of a commitment, ready to do. May be taken. |
| Waiting for | waiting | Depends on someone or something outside. The task says on whom and since when. |
| Done | done | Finished. Closing clears the assignment. |

Hestana requires a status for each of its six states, with one default per state, so the Space also keeps **doing** (marks the action being worked now) and **canceled** (decided not to do). They are not lists. Do not create parallel lists; if a Space has other codes, map them to these states.

## Capture
Anything with attention goes to the Inbox without judging it: a title and, if useful, a line of context. Anyone, person or agent, may capture. Capturing is not committing.

## Clarify
For each Inbox item: is it actionable?
- Not actionable: cancel it, move it to Someday/maybe, or keep it as a document outside the task list.
- Actionable, one step: rewrite the title as the next physical action, with a verb. Two minutes or less: do it now. Someone else's: Waiting for, naming who and since when. Otherwise Next actions.
- Actionable, several steps: a project.

Only the person moves an item out of the Inbox or decides it is Someday/maybe. An agent prepares the clarification as a comment (is it actionable, intended result, proposed next action).

## Projects and next actions
A project is a commitment of more than one step: a task with subtasks, which cannot be taken itself. Each subtask is an action. Steps that depend on each other get prerequisites; parallel steps get none. A project always has a next action: its first unblocked subtask in Next actions. A project without one is stalled; the weekly review finds it. The person closes the project when its outcome is reached, or cancels it.

## Context
The only context the server understands is **availability**: people (`HUMAN`), actors (`ACTOR`) or anyone (`ANY`). Use it as GTD context: what only a person can do on the spot against what an agent can take. No other context field exists; do not put context words in titles as if they were filterable.

## Do
Choose from Next actions by what is possible now, time and energy, and priority. A person takes an action by assigning it to themselves; an agent takes only actions the person opened to actors. Taking is assigning with a deadline matched to the work; assign again before it passes to extend, and a passed deadline reads as free. Taking does not change the status: move to the doing status when work starts, to Done when finished with the result recorded. A released action keeps its status.

## Review
A system that is not reviewed stops being trusted. The weekly review: empty the Inbox, give every project a next action, chase every Waiting for, look at Someday/maybe for what to activate or drop. The person does it. An agent may prepare a digest of staleness and must not move anything.

## Out of scope
Areas of focus, horizons, tickler files and calendars. The method does not authorise any action and does not let an agent decide what matters; system rules, access and project policy govern.
