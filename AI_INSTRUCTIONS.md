# AI_INSTRUCTIONS.md

Essential context reading order:
1. `_context/CHARTER.md` — Project definition, design principles, architecture, boundaries

## Working Rules

- Read the charter before starting any work
- Follow the decision process: propose decisions in `temporal/decisions/00-proposed/`, get approval before implementing
- Discussions go in `discussions/` using the `DISC-CH-YYYY-MM-DD-NNN_topic.md` naming convention
- Decisions use `DEC-CH-YYYY-MM-DD-NNN_topic.md` naming convention
- Keep the core thin — if it could be an extension, it should be
- Extension failure must never break the core
