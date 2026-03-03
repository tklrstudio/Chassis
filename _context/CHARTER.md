# Chassis Charter

**Purpose:** An open-source podcast show management platform — the frame that recording, transcription, and other tools bolt onto
**Status:** Canonical
**Workspace Code:** CH
**Created:** 2026-03-04
**Last Updated:** 2026-03-04
**Version:** 1.0.0

---

## Purpose

Chassis exists because podcast production involves more than recording. Managing shows, inviting guests, tracking episodes, editing, transcribing, and publishing are all separate concerns — but today's tools bundle them into monolithic platforms where one failure breaks everything.

Chassis is the coordination layer. It manages shows, episodes, and workflows. Recording, transcription, editing, and publishing are handled by extensions that plug in — starting with Open Booth (recording) and Say What? (transcription).

Chassis is **open source**. Anyone can use it, self-host it, extend it, or build on it.

---

## Success Criteria

- A podcaster can create a show, invite a guest, and manage an episode workflow through Chassis
- Extensions (Open Booth, Say What?) integrate cleanly through defined plugin interfaces
- A new extension can be built and plugged in by reading the extension API docs
- The platform is self-hostable — no mandatory cloud dependency
- Failure in one extension does not break the core or other extensions

---

## Boundaries

What Chassis is **NOT**:

- **Not a recording tool** — that's Open Booth. Chassis coordinates; it does not capture audio.
- **Not a transcription tool** — that's Say What?. Chassis triggers and manages transcription through the extension interface.
- **Not a monolith** — every major capability is an extension, not a built-in. If it could reasonably be a plugin, it should be.
- **Not a SaaS product** — open source, self-hostable. No billing infrastructure, no multi-tenant architecture.

---

## Design Principles

In priority order:

1. **Extensions over builtins** — if a capability could be a plugin, it must be. The core is thin.
2. **Decoupled by design** — extension failure is isolated. Recording breaking does not affect episode management.
3. **Open source first** — MIT licensed. The community can extend, fork, and contribute.
4. **Self-hostable** — works on your own infrastructure. No mandatory external services.
5. **Honest failure** — if something goes wrong (extension down, upload failed, transcription errored), surface it clearly.
6. **AI-friendly docs** — written so a non-technical user can get help from an AI assistant without additional context.

---

## Architecture

Chassis follows a WordPress-like plugin model: a thin core platform with extension points.

```
chassis/
├── core/                    # Show management, episode workflows, guest invitations
└── extensions/              # Plugin interface — each extension is a separate tool
    ├── open-booth/          # Recording (via Open Booth)
    └── say-what/            # Transcription (via Say What?)
```

**Key architectural decisions:**
- **Plugin interface:** Extensions register capabilities, receive events, and exchange data through a defined API
- **Decoupled deployment:** Extensions can run on separate infrastructure — Chassis doesn't assume co-location
- **Data ownership:** Each extension owns its data. Chassis coordinates but does not store audio, transcripts, etc.

**Note:** This architecture is directional. The specific plugin interface, tech stack, and data model are future decisions. This charter defines the shape, not the implementation.

---

## Quality Criteria

Output is good when:
- The core platform works without any extensions installed
- An extension can be added or removed without breaking the core
- A new contributor (human or AI) can understand the architecture by reading this charter
- The extension API is documented well enough to build a new plugin

---

## Failure Patterns to Watch

- **Monolith creep** — building capabilities into the core that should be extensions. Every "just add it to core" is suspect.
- **Premature architecture** — designing the perfect plugin system before building the first working feature. Ship something, then refine the interfaces.
- **Scope creep toward SaaS** — any suggestion to add billing, multi-tenant infrastructure, or managed hosting should be questioned. That is not what this project is.
- **Feature over reliability** — new extensions should not compromise the core workflow. If they do, the isolation model is broken.
- **Doc drift** — docs must stay current. An extension without documentation is not done.

---

## Binding Rules

- Extensions communicate through defined interfaces, never by reaching into each other's internals
- Core must function without any extensions installed
- Errors from extensions must be surfaced to the user — no silent failures
- Update docs whenever behaviour or interfaces change

---

## Extension Ecosystem (Planned)

| Extension | Purpose | Status |
|-----------|---------|--------|
| Open Booth | Recording — browser-based, chunked upload, dual encoder | Published (separate repo) |
| Say What? | Transcription — audio to text | Published (separate repo) |
| Editor | Auto-edit — silence removal, level normalisation | Future |
| Publisher | Platform publishing — push to podcast hosts | Future |

New extensions must not compromise core reliability or require changes to existing extensions.

---

*Chassis is open source. Built for podcasters who want control over their production workflow. Review this charter when the scope or architecture changes materially.*
