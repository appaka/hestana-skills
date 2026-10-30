# Binding to the Space's methodology

A Space's methodology is a setting the Space owner chooses in the app. The server stores it as a label and does not interpret it. An agent cannot set it.

## Reading it

Call `spaces_get` for the Space. The field is `methodology: { id, version, skill, summary } | null`.

- `id` and `version`: what the owner chose (for HAD, `human-agent-development` and a version).
- `skill`: the name of the optional skill for that methodology; null if the catalog does not know the `id`.
- `summary`: one short sentence of what is expected. It lets an agent without the skill know the expectation.

`spaces_list` returns the same field for each Space without `summary`. The server instructions may also show it beside each Space.

## Cases

1. **HAD (`human-agent-development`).** Apply this skill. If the Space's `version` is not 0.7.0, say so once ("the Space chose HAD <version>, this skill is 0.7.0; the method may differ in details") and continue. The Space's version is information, not a gate, and this skill does not stop on any difference.
2. **Another methodology.** Do not apply HAD rules (its roles, vocabulary, templates or completion rules). Tell the person which skill exists for that methodology (the `skill` field) and that installing it is their choice. Meanwhile work with Hestana's tools, the statuses by name, and the `summary`. The generic Hestana mechanics in [hestana-mechanics](hestana-mechanics.md) remain valid, but they are not that method.
3. **None.** Say so, propose HAD if the situation fits (several people and agents, shared tasks, handoffs, human decisions), and ask. Choosing is the owner's action in the app; you cannot do it, and you do not write a document to simulate it. If the person asks you to follow HAD for this piece of work without it being set, do so and state that this is not the Space's setting.
4. **Unreadable.** If `spaces_get` fails or the field is absent (an older server), say the methodology could not be read, ask the person, and continue without blocking.

## Run-specific choice

The person may tell you in conversation to use HAD for one run. That applies to the run only and changes nothing in the Space. If the Space's own methodology is different, mention the difference and follow the person's instruction.

## Never

Do not infer the methodology from a directory, an old document, past use or an installed skill. Do not claim the Space "adopted" anything that `spaces_get` did not return. Do not refuse or delay work because the skill or the setting is missing.
