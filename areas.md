> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/areas) · 🇷🇺 [Русская версия](ru/areas.md)

---

## Information Areas

The standard defines optional information areas. A team creates only what it needs. Structuring information into distinct areas realizes the [“Distinguish information types” principle](./intellectual-space.md#principle-classified): durable knowledge, current state, and rules governing changes serve different purposes. Canonicality belongs to particular knowledge and its source, not to an area. An area can be represented by a single file or by a directory with `INDEX.md`; its structure should be organized modularly from the start, designing sections with future decomposition in mind. Paths in the table show directory-based setups:

| Area | Purpose | Example Contents |
| --- | --- | --- |
| `FISS/knowledge/subject/` | Domain knowledge the project operates within | Concepts, business rules, processes, domain invariants |
| `FISS/knowledge/project/` | Durable knowledge about the project itself | Architecture, project terms, environment, conventions, practices |
| `FISS/state/` | Current information that can affect work | Handoff synchronization state, open questions, active risks, temporary constraints |
| `FISS/overrides/` | Project rules for applying agent skills | Skill behaviors and lifecycles, templates, verification criteria, human governance |
| `FISS/human/knowledge/` | Standalone knowledge primarily for humans | Observations, personal context, explanatory notes |
| `FISS/human/hmm/` | Derived Human Mental Model representations | Domain concept maps, architecture diagrams |

The team may add custom areas. Standard structural and navigation rules apply to them.

### Knowledge: Domain and Project

`FISS/knowledge/subject/` answers the question **"What must be understood about the domain?"** It describes entities, terminology, processes, rules, and invariants. The name `subject` is not tied to any mandatory methodology, including DDD.

`FISS/knowledge/project/` answers the question **"What must be known about the project structure and workflows?"** It describes architecture, component relationships, environments, tooling, conventions, common pitfalls, and known workarounds.

The `FISS/knowledge/` directory functions as a container for knowledge areas. Inside it, a project MUST establish a `subject` area (directory `subject/` or file `subject.md`), a `project` area (directory `project/` or file `project.md`), or both. Placing files directly in the root of `FISS/knowledge/` (such as `FISS/knowledge/architecture.md` or `FISS/knowledge/rules.md`) is prohibited by the standard — all durable knowledge must belong to either domain knowledge (`subject`) or project knowledge (`project`).

Glossaries can span both areas. Domain terms belong in `FISS/knowledge/subject/`, while component names, internal abbreviations, and project-specific terms belong in `FISS/knowledge/project/`. If a term shares the exact meaning in both areas, define it once and cross-reference. If a word has different meanings, define each separately and explicitly identify its applicable scope.

Durable knowledge may also evolve over time. Its distinction from current state lies in purpose: it supports understanding and working on the project across multiple tasks.

### State

`FISS/state/` describes the **current situation** that can affect work: open questions, active risks, and temporary constraints.

FISS requires handoff semantics, not a particular file. A project may represent the handoff in an existing canonical state mechanism or in a separate operational artifact. `FISS/state/fiss-handoff.md` is a recommended default, not a mandatory path; resolve any artifact location using the standard operational-artifact rules and expose it through applicable navigation. The record identifies the FISS synchronization state and current work item, linking to an external canonical task source rather than duplicating task status or maintaining a task registry.

The state is `synchronized` when FISS-relevant outcomes are recorded and the space is ready for another independent work item. It is `pending` while a work item is current or its outcomes remain to be synchronized, and `unresolved` when a blocker needs a decision. Before starting new independent work, an agent determines the current state. From `synchronized`, the agent records the new work as `pending` before substantive work unless an applicable project-defined mechanism performs that transition. The identified work may continue while `pending`; different independent work may not begin. Projects may define another transition mechanism, but hooks, CI, version control, and task trackers are not required by FISS.

Standalone state documents may reside directly within `FISS/state/`. A registry or collection of items (such as ADRs, risks, open questions, or tasks) MUST NOT be scattered loosely across `FISS/state/`. Such a registry MUST be structured either as a dedicated composite area with its own `INDEX.md` (e.g. `FISS/state/adr/`, `FISS/state/risks/`, `FISS/state/open-questions/`), or as a consolidated single-file area (e.g. `FISS/state/open-questions.md`).

If current state is already tracked in an external tool, link to that authoritative source. For example, when tasks are tracked in an issue tracker, FISS must not create a duplicate tracker for the same items. Rules for transitioning state, if the project customizes skill behavior, reside in `FISS/overrides/`.

### Material Primarily for Humans

The entire intellectual space should remain accessible to humans. The `FISS/human/` area is used when a team wants to separate materials that do not need to be included in routine agent context.

- `FISS/human/knowledge/` contains standalone knowledge primarily intended for people. Like other FISS knowledge, it is canonical by default unless explicitly marked as derived.
- `FISS/human/hmm/` contains derived Human Mental Model representations that help humans navigate and reason about complex systems. This area is intended for projects that need such representations; there is no need to create it prematurely.

The `FISS/human/` directory also functions as a container. Inside it, a project MUST establish a `knowledge` area (directory `knowledge/` or file `knowledge.md`), an `hmm` area (directory `hmm/` or file `hmm.md`), or both. Placing files directly in the root of `FISS/human/` outside these areas is prohibited.

HMM representations can be concept maps, architecture overviews, and dependency charts. Every HMM material must contain the exact English marker `Derived from:` followed by Markdown links to all material sources needed to understand and verify its origin. Sources are not limited to `FISS/human/knowledge/`; they may reside in `FISS/knowledge/project/`, `FISS/knowledge/subject/`, `FISS/state/`, `FISS/human/knowledge/`, or another relevant location. When a source changes, related HMM materials should be reviewed. Their existence alone never makes them canonical.

The name `FISS/human/` denotes intended audience and purpose, not access restriction. Document applicability is determined by read conditions and project policies.
