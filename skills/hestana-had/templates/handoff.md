# Result and handoff template

Append concise durable context to existing work when yielding, changing executor or finishing (`notes_add` with `label: handoff`). Keep the canonical specification and accepted decisions directly retrievable.

Replace braces with actual context and remove unused prompts. This is a writing aid, not a server schema or an authorization.

```markdown
Result/state: {what exists now and what remains; implementation, verification, acceptance and release stated separately; last observed status code}

Agreement: {current task/specification revision, accepted decisions, method (human-agent-development, version read from the Space) and applicable policy}

Artifacts and evidence: {accessible artifact/commit references and revisions; criterion/check, actual outcome, verifier/time and limitations}

Questions/blockers: {each unanswered question (a comment that mentions a person) or missing input, affected action and the person asked if known; otherwise none}

Coordination: {whether you still hold the task (assigned, with its deadline) or released it or closed it; do not claim a description edit releases it}

Next action: {one concrete continuation step, inputs to re-read and any revalidation needed}
```
