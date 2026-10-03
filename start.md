> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/start) · 🇷🇺 [Русская версия](ru/start.md)

---

## Quick Start

A conforming minimal structure consists of two required files:

```text
FISS/
├── INDEX.md
└── BOOTSTRAP.md
```

- **`FISS/INDEX.md` — Entry point.** Contains links and read conditions for materials.
- **`FISS/BOOTSTRAP.md` — Baseline context.** Provides initial orientation in the project.

Minimal `FISS/INDEX.md`:

```markdown
# Project Intellectual Space

- [Baseline Context](BOOTSTRAP.md)
  Read when: beginning work on the project or onboarding to the space.
```

In `FISS/BOOTSTRAP.md`, briefly explain the purpose of the project, key rules and constraints, critical definitions, and peculiarities without which the project could easily be misunderstood.

This file must remain concise. Information needed only for a specific area of work should be placed in that area. This approach implements the [“Start small” principle](./intellectual-space.md#principle-compact): in a small project, all substantive content can fit within `FISS/BOOTSTRAP.md`; `FISS/INDEX.md` remains mandatory. Artificially splitting short text is not required — information and structures are added only when actual content or context needs arise.

For the team, it is recommended to add a link to `FISS/INDEX.md` in the project README or another familiar starting point. If the project uses `AGENTS.md` or another root instruction file for AI agents, that file MUST direct agents to `FISS/INDEX.md` and MUST NOT duplicate space content.
