# Research walkthrough

Illustrative scenario: determine whether an existing outbound notification channel provides retrievable delivery evidence. Fictional; not a finding about Hestana and not a message to a person.

## Scope and stop condition

Question: what evidence can the documented channel return for attempted, delivered and read notifications, and what stays unobservable?

Boundary: official documentation plus an already authorized non-production fixture, if available. Live messages, account configuration and production changes are excluded. If the fixture is unavailable, finish the documentation part and report the gap; do not invent test results. Stop when the documented events are mapped, available fixture observations are recorded, and remaining unknowns and their consequences are explicit. A separate real integration validation may still be needed.

The researcher takes the investigation with `task_assign` and a deadline matching the boundary; the accountable person stays its owner. If it needs longer, assign again; if it stops unfinished, `task_release` and leave a handoff.

## Evidence and decision support

The report links dated sources and fixture artifacts and distinguishes what documentation promises, what the fixture showed and what is inferred. A valid result may be that no supported read receipt is available, or that the evidence cannot settle it. The recommendation says which workflow claims are supportable and proposes a next step; it does not turn a transport receipt into the answer to a question asked of a person, select a provider or authorize deployment.

An open decision such as "Is delivery without a read receipt sufficient for this project?" is a comment that mentions the designated decision-maker and awaits an answer. The report may be complete while adoption of its recommendation stays blocked by that decision; the pending question does not pause the research.

## Review and handoff

Review checks the question, boundary, traceable evidence, uncertainty and practical recommendation. No code harness is invented for information-only work; any repository change or experiment keeps its own rules. The reviewer's outcome is a comment on the task. The result names what was established, which claims remain unverified and the next decision. If implementation is later authorized, its task links this report and the accepted decision; finishing the research does not enqueue it.
