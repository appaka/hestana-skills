# Executing a next action

1. **Pick.** `task_next` suggests takeable work without reserving it (open state, no effective assignment, no unfinished prerequisites, no subtasks, availability that allows you); `null` means nothing is eligible for you now. If the person named a task, use that. Choose by what is possible now and priority, not by what looks interesting.
2. **Check.** `task_get`: `availability`, `ownerUserId` (the accountable person, who stays accountable whoever works), `blockedBy`, status. Not in Next actions: it is not offered; say so and stop. Held by someone else: re-read and decide; never replace the holder unless a person told you to.
3. **Take before changing anything.** `task_assign` for yourself (omit assignee) with `until`. Then `task_context` with only `taskId`. After any gap or after taking it again, re-read `task_context` and the comments (`notes_list`) before writing a result or changing the task: the answer may already be there.
4. **Start.** `task_set_status` with the doing code when work really starts, passing `expectedVersion` as last observed.
5. **Work** within the task as written. If its title is not a physical action or the outcome is unclear, do not guess: comment with a proposed clarification and mention the owner (`awaitsAnswer`) or stop with a handoff.
6. **Exits**
   - Finished: write the result and evidence, `task_set_status` to done. Then the handoff, with the state the server returned.
   - Depends on someone or something outside: `task_set_status` to the waiting code; description (via `task_update`, full description) says who and since when; handoff; `task_release` unless the person wants you to keep it.
   - Need a person's answer but work goes on: comment mentioning them with `awaitsAnswer`; not a Waiting for entry.
   - Cannot finish: handoff, `task_release`; the task keeps its status; move it back to Next actions only if it should be picked again.
   - Not worth doing / failed: `task_set_status` to canceled with the reason in the result. `failed` is not a state.
7. **Never** close a project because its subtasks are closed; say the outcome may be reached and let the person close it. Never move something out of the Inbox or into Someday/maybe yourself.

Waiting for follow-up: when asked to chase, read the entry's who and since when, check `notes_list` for news, and report; contacting someone is the person's call unless they asked you to and a tool of yours does it within their request.
