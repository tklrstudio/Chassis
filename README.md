# Chassis

An open-source podcast show management platform — the frame that recording, transcription, and other tools bolt onto.

## What is Chassis?

Chassis manages the production side of podcasting: shows, episodes, guests, and workflows. It doesn't record audio or transcribe it — those are handled by extensions that plug in.

Think of it like WordPress for podcast production: a thin core with a plugin architecture.

## Extension Ecosystem

| Extension | Purpose | Status |
|-----------|---------|--------|
| [Open Booth](https://github.com/tklrstudio/Open-Booth) | Browser-based recording — chunked upload, dual encoder, IndexedDB local storage | Published |
| [Say What?](https://github.com/tklrstudio/transcribe) | Transcription — audio to text | Published |
| Editor | Auto-edit — silence removal, level normalisation | Planned |
| Publisher | Push to podcast hosts | Planned |

Each extension stands alone. Together with Chassis they form a complete open-source podcast production stack.

## Status

Chassis is in the design phase. The charter and architecture are defined; implementation has not started.

## Repo Structure

```
chassis/
├── CLAUDE.md                # AI entry point → AI_INSTRUCTIONS.md
├── AI_INSTRUCTIONS.md       # Context loading and working rules
├── _context/
│   └── CHARTER.md           # Project definition, design principles, boundaries
├── temporal/
│   └── decisions/           # Architectural and governance decisions
└── discussions/             # Design conversations and exploratory sessions
```

## How to Work Here

Read `_context/CHARTER.md` for the project definition, design principles, and boundaries.

## License

MIT
