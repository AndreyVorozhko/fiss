> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/ecosystem) · 🇷🇺 [Русская версия](ru/ecosystem.md)

---

## FISS Tool Ecosystem

To support the standard, automate conformance verification, and streamline project workflows, an ecosystem of companion tools is available.

### FISS Linter (`fiss-lint`)

**[`fiss-lint`](https://github.com/AndreyVorozhko/fiss-lint)** is the official static analysis and linting tool for FISS intellectual spaces.

Key capabilities:
- **Structural verification:** verifies required files (`FISS/INDEX.md`, `FISS/BOOTSTRAP.md`) and directory layouts (`knowledge/`, `human/`, `state/`).
- **Navigation validation:** enforces the strict two-line index format and the mandatory non-localized `Read when:` marker.
- **Link integrity:** checks that all index targets resolve to existing files and validates `Derived from:` markers for derived knowledge.
- **CI/CD integration:** runs fast in developer terminals or automated CI/CD pull request workflows.

Project repository: [github.com/AndreyVorozhko/fiss-lint](https://github.com/AndreyVorozhko/fiss-lint)

### Agent Skills (`fiss-skills`)

**[`fiss-skills`](https://github.com/AndreyVorozhko/fiss-skills)** is a collection of specialized agent skills for AI assistants working within FISS intellectual spaces.

Included skills:
- **`fiss-init`:** initializes a new conforming FISS intellectual space from scratch. Scaffolds root files, analyzes project to discover work classes (FISS-relevant vs operational), creates work classification taxonomy, establishes entry points, and configures handoff mechanisms. Use when a repository does not have a conforming FISS space.
- **`fiss-maintain`:** maintains intellectual space continuity across task transitions. Distinguishes FISS-relevant work from operational work, manages handoff state transitions (`pending` → `synchronized`) for work that produces FISS-relevant outcomes, maintains work classification taxonomy, updates navigation and links, resolves operational artifact locations, and persists task context.
- **`fiss-validate`:** performs read-only structural and semantic validation of the intellectual space against standard invariants without mutating files. Verifies work classification taxonomy, checks that handoff gate requirements apply only to FISS-relevant work, and validates that operational work correctly bypasses gate transitions, complementing static linter checks.

Project repository: [github.com/AndreyVorozhko/fiss-skills](https://github.com/AndreyVorozhko/fiss-skills)
