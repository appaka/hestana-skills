# hestana-skills

Optional skills for agents that work in [Hestana](https://hestana.com) Spaces, one complete skill per methodology (ADR-696):

| Skill | Methodology | Version |
|---|---|---|
| `hestana-kanban` | Kanban | 0.1.0 |
| `hestana-gtd` | Getting Things Done | 0.1.0 |
| `hestana-had` | Human and agent development | 0.7.0 |

Each one teaches how to plan and how to execute work under that method, with the Hestana mechanics it needs. They are optional: an agent without any works with Hestana's tools, and a skill never blocks work. The skill reads the Space's methodology from `spaces_get` (`methodology`).

Install one with `npx skills add appaka/hestana-skills@<skill>` once this repository is published.

MIT licensed.
