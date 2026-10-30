# Human decision template

Use for a specific unanswered choice. Ask it as a comment on the affected task that mentions the person and awaits an answer (`notes_add` with `mentions: [{ userId, awaitsAnswer: true }]`); substantive option analysis or other human production may instead need a linked task. This is not an approval mechanism for a governed action.

Replace braces with actual context and remove unused prompts. This is a writing aid, not a server schema or an authorization.

```markdown
# {Decision needed}

Question reference: {stable local reference or comment, affected task and contract revision}

Question: {one focused question with enough context to answer}

Why now: {what action/result depends on this; other blockers that will remain}

Options: {feasible alternatives, recommendation and relevant consequences; include no-change/defer when meaningful}

Authority: {the person who decides this and how they are asked, or "unknown - ask the accountable person whom to ask"}

Answer needed: {what concrete choice resolves this question; deadline only if established}

Resolution: {pending until an authorized reply; later record answer, responder, time/source and question/contract reference}

Effect and handoff: {which requirement changed, affected work/revalidation and next action after all blockers are reconciled}

A reply resolves this question only. Do not treat it as completion of separate human work, permission for unrelated actions or a way to clear independent blockers.
```
