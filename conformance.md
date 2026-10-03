> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/conformance) · 🇷🇺 [Русская версия](ru/conformance.md)

---

## Conformance Checklist

This checklist consolidates the requirements for validating project conformance:

- The project root contains `FISS/INDEX.md` and `FISS/BOOTSTRAP.md`.
- The root index links to `FISS/BOOTSTRAP.md` with a read condition requiring it before work begins on the project.
- The root index is recommended to reference the adopted standard edition: official website `https://fiss.vorozhko.ru` and/or GitHub mirror `https://github.com/AndreyVorozhko/fiss` as fallback.
- Every used area is reachable via navigation from the root index; composite areas contain an `INDEX.md` linking to their contents.
- Every index navigation link is formatted as a strict two-line entry with the mandatory English read condition marker `Read when:` defining context applicability, and resolves to an existing target.
- If overrides are used, the root index links to `FISS/overrides/INDEX.md` with the read condition "Read when: using or preparing to use any skill"; agents check applicable documents before running skills.
- If skills share operational artifacts, default filenames and path override rules are coordinated between skills and project documentation.
- Single-file areas may use project-defined filenames; containers without an index are reachable through navigation of their enclosing area.
- If the `FISS/knowledge/` directory is used, it contains only a `subject` area (directory or file) and/or a `project` area (directory or file); files do not reside directly in the root of `FISS/knowledge/`.
- If the `FISS/human/` directory is used, it contains only a `knowledge` area (directory or file) and/or an `hmm` area (directory or file); files do not reside directly in the root of `FISS/human/`.
- If the `FISS/state/` directory is used, individual state documents may reside directly in it, while item registries (ADRs, risks, open questions) are organized as composite areas with `INDEX.md` or consolidated single files, rather than scattered loose files.
- The FISS handoff state is recorded in one resolved logical artifact or canonical state mechanism; it identifies the current work item (or links to its canonical source) and does not duplicate task status or create a task registry.
- Before new independent work begins, the agent determines the handoff state. If no applicable project-defined transition mechanism exists, the agent records the new work as `pending` before substantive work when the state is `synchronized`; it does not start different work from `pending` or `unresolved`. The identified current work may continue while `pending`.
- Work is handed off as `synchronized` only after its FISS-relevant outcomes have been captured, delegated, or explicitly classified as requiring no persistence. A blocking decision leaves the state `pending` or `unresolved`.
- Projects may define transition enforcement, but FISS does not require a hook, CI/CD, version control, task tracker, or other enforcement infrastructure.
- Indexes focus on navigation, while `FISS/BOOTSTRAP.md` provides concise baseline context.
- Knowledge without `Derived from:` is canonical by default; no separate canonical marker is required.
- Every derived material uses the exact English marker `Derived from:`, followed by links to all material sources, and those links resolve when the sources are part of the project.
- Every material in `FISS/human/hmm/` is marked as derived and links to its source or sources.
- The same knowledge is not maintained by multiple independent canonical sources; suspected semantic duplication that cannot be established mechanically is reviewed by a person.
- Established source rules are applied when sources conflict; a conflict without such a rule requires an explicit project decision.
- If a root agent instruction file (`AGENTS.md`) is present, it directs agents to `FISS/INDEX.md` without duplicating space content.
- If a task workflow is documented, applicable rules for handling operational artifacts are specified.

Other areas and mechanisms are introduced as needed.

Structural checks can be automated. A linting tool (e.g., [`fiss-lint`](https://github.com/AndreyVorozhko/fiss-lint)) can verify required files, link integrity, the two-line navigation format, presence of the mandatory `Read when:` marker, and naming conventions.

Mechanical validation does not assess accuracy, relevance, or completeness of knowledge. Those responsibilities remain with the project team.
