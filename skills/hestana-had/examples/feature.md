# Feature walkthrough

Illustrative scenario: a project member wants to save personal filters in the task list. Names and decisions are fictional, not accepted requirements. Reading this creates no tasks and posts no comments.

## Capture and discovery

Initial idea: let a person return to the task view they use every day. The assistant finds the current task-list specification and related work, then records the desired outcome: a member can reopen a personal saved filter in the same project.

| Ref | Question | Example authority and state | Effect |
|---|---|---|---|
| Q1 | Are filters personal or shared? | Designated product decision-maker; answered: personal only | Allows specification of personal ownership |
| Q2 | What if a saved filter names a capability that was removed? | Same decision-maker; pending | Blocks acceptance and implementation of that fallback |

The brief records Q1's answer and source as an accepted decision. Q2 stays visible. No default is inferred from silence. Read-only investigation of how filters serialize may continue if authorized.

## Investigation and plan

A bounded investigation asks whether the existing query representation can round-trip supported filters; its output lists supported fields, incompatibilities and code references. A proposed first slice supports one person's filters within the existing project boundary; sharing and a new role model are excluded. The plan avoids a long chain of speculative tasks.

The slices are saved in a backlog status, so nobody can take them. After the decision-maker answers Q2, the accepted brief records the behaviour and version. Only then can dependent work be prepared and published (moved to an open status) under current authority. Alex, the accountable person, owns each slice; the owner is not necessarily the one who will do the work.

## Execution and human help

An authorized worker takes the first slice with `task_assign` and a deadline matching the work: Alex stays owner, the worker is the assigned principal. It recovers the brief, decisions and repository policy (`task_context`) and moves the task to a doing status. During implementation it hits an unexpected choice, whether a renamed filter label must be unique. It asks Q3 as a comment that mentions the decision-maker and awaits an answer, with the affected action, options and artifacts, and continues with whatever does not depend on Q3. Q3 does not pause the task or end the reservation. If work runs past its deadline the worker assigns again to extend it; if nothing else can proceed, it leaves a handoff and calls `task_release`.

If an access prerequisite is also outstanding, answering Q3 does not resolve it. Each question and prerequisite resolves on its own. If a designer must produce an interaction proposal, that is separate human work with an output, a linked task, not a question answered by a mention.

## Verification and acceptance

Once the decisions are resolved, observable checks include reopening the saved view, isolating filters between users and projects, and the specified invalid-filter behaviour. The worker records checks and review as evidence in the task result and comments, against the accepted brief revision; these do not replace repository requirements. The outcome is accepted by the authority designated under current policy only after its own behaviour is demonstrated. If deployment was excluded, the result says the implementation was verified but is not in production. Closing the task clears the worker's assignment.

A replacement worker can find the accepted brief and revisions, Q1 to Q3 and their disposition, prerequisite outputs, artifacts, review feedback and next action without the original chat.
