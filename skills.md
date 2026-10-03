> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/skills) · 🇷🇺 [Русская версия](ru/skills.md)

---

## FISS and Agent Skills

Skills belong to the intellectual space in a broad sense. However, skill formats, storage, installation, discovery, and invocation lie outside FISS. The standard does not require storing skills inside `FISS/`.

Interactions with external skills rely on the [“Keep external mechanisms independent” principle](./intellectual-space.md#principle-composable): external mechanisms remain independent, while the standard supports a project-level override mechanism to adapt their behavior without modifying the mechanisms themselves.

If the project uses overrides, the root index must include a link to `FISS/overrides/INDEX.md` with the read condition "Read before using any skill." For example:

```markdown
- [Project Overrides](overrides/INDEX.md)
  Read when: using or preparing to use any skill.
```

### Operational Artifacts

An **operational artifact** is an artifact that is not merely descriptive, but is actively utilized during work as a functional component of the process.

An intellectual space comprises more than static knowledge and instructions. It includes operational artifacts that guide a task through its lifecycle. For example, a statement defines the task, a plan guides execution, and verification evidence substantiates task completion.

One possible workflow:

```text
intent → statement → research → decisions → plan → changes → result → verification
```

This is an illustrative workflow, not a FISS mandate. Process stages may produce operational artifacts; a dedicated file for each stage is not required. The operational nature is determined by an artifact's role in the workflow, not its format, directory, or retention period.

A skill must reference operational artifacts by logical purpose and may define a **default filename**. For example, a planning skill creates a plan in `plan.md`, while an execution skill reads and executes that artifact. Skills operating on the same artifact must use consistent logical naming and default filenames, or adhere to project-defined mappings.

The project specifies the location of operational artifacts in a relevant document in `FISS/overrides/`:

```markdown
Operational artifacts for the current task are located in `_currenttask/`.
```

In this case, the filename `plan.md` specified by the skill resolves to `_currenttask/plan.md`.

```markdown
The task plan operational artifact is located at `_currenttask/task-plan.md`.
```

This rule specifies the full path for a particular artifact and overrides its default filename. If both rules exist, `_currenttask/task-plan.md` is used for the plan, while other operational artifacts use the shared directory and their default filenames. Paths in these examples are relative to the project root.

Before reading or creating an operational artifact, an agent MUST resolve its location in the following order:

1. Explicit project path for the specific logical artifact;
2. Shared task-artifact directory plus the skill default filename;
3. Repository convention or skill default behavior.

Skills using the same operational artifact within a task must resolve to the same location. If an existing artifact is in another location or rules conflict, resolve discrepancies via canonical source rules rather than creating duplicate instances. For parallel tasks, provide separate task workspaces or another unambiguous method to distinguish artifacts.

### Project Overrides

`FISS/overrides/` contains project-specific overrides to the rules and behavior of **mechanisms external to the project and its intellectual space** that are used by the project. For example, skills. Project-specific rules and behaviors that do not override external mechanisms should be stored in `FISS/knowledge/project/`.

A skill should embody portable reasoning and procedures. A project may tailor where artifacts reside, how records are formatted, what constitutes acceptable verification, and when an agent must pause for human review. These project-specific rules should not be hardcoded into skills, which would undermine portability.

For such rules, an optional composite area `FISS/overrides/` is recommended:

```text
FISS/
├── INDEX.md
├── BOOTSTRAP.md
└── overrides/
    ├── INDEX.md
    ├── skills/
    │   ├── open-questions.md
    │   ├── adr.md
    │   ├── risks.md
    │   ├── task-execution.md
    ├── governance.md
    ├── artifacts.md
    ├── templates.md
    ├── verification.md
    ├── orchestration.md
    ├── context-and-memory.md
    └── style.md
```

This is an illustrative structure, not a mandatory set of files. Create only documents where the project genuinely customizes or standardizes a rule. `FISS/overrides/INDEX.md` remains the single entry point as the area expands. Maintain a single entry point, avoiding parallel competing rule definitions.

`FISS/overrides/INDEX.md` links to active override documents with read conditions. Applicability is determined by the subject matter, not by skill names: skills can be renamed, combined, or refactored. Skill names are not needed for navigation. For example:

```markdown
# Project Overrides

- [Open Questions](skills/open-questions.md)
  Read when: adding, reviewing, or resolving open questions.
- [Verification Criteria](verification.md)
  Read when: planning verification and confirming completion.
```

In this example, `skills/` is a container within `FISS/overrides/`: links to its documents reside in `FISS/overrides/INDEX.md`. A standalone `FISS/skills/` area is not created. Rules, state transitions, and lifecycle behaviors for skills reside in overrides, while active questions, risks, and decisions belong in their respective areas or external tools.

Before using any skill, an agent MUST read the override entry point if it exists, and select applicable documents according to read conditions. Reading all override documents is not required. This is a foundational rule for agent-project interaction that need not be repeated in each skill.

In the absence of an explicit rule, the agent applies explicit project rules, followed by detected repository conventions, and finally skill defaults. An override replaces only the behavior it explicitly defines; other skill rules remain intact. Conflicts with other explicit project rules are resolved via source rules. Overrides do not bypass runtime execution limits; if a rule cannot be applied, the agent must report the situation to a human.

Overrides are canonical human-readable documents, not opaque variable tables. They articulate rules directly and reference existing knowledge, external systems, and project artifacts. A separate YAML configuration with identical settings is unnecessary. Where tools require machine formats, they must be generated as derived knowledge of canonical documents and contain `Derived from:` with links to those documents.

### What Can Be Overridden

The following categories outline common project rule customizations. All paths in the last column are relative to the project root:

| Category | What the Document Governs | Example Files |
| --- | --- | --- |
| Skill Lifecycles and Behaviors | States, transitions, resolution criteria for ADRs, open questions, risks, task execution, terms, mental model reconciliation, branches and merges | `FISS/overrides/skills/open-questions.md`, `FISS/overrides/skills/adr.md`, `FISS/overrides/skills/risks.md` |
| Governance and Autonomy | Mandatory human approvals, agent autonomy levels, human review criteria, acceptable plan deviations | `FISS/overrides/governance.md` |
| Artifacts and Paths | Locations of ADRs, domain knowledge, open questions, risks, glossaries; shared task artifact directory and specific artifact paths | `FISS/overrides/artifacts.md` |
| Templates and Formats | Structures of ADRs, task plans, risk logs, prescriptive rules, commit messages, PR descriptions | `FISS/overrides/templates.md` |
| Verification | Verification commands, acceptable evidence, completion criteria, required independent reviews | `FISS/overrides/verification.md` |
| Orchestration | Retry limits, model and role assignments, disambiguation rules, concurrency, worktrees | `FISS/overrides/orchestration.md` |
| Context and Memory | Context compaction thresholds, checkpoints, knowledge consolidation, obsolescence signals | `FISS/overrides/context-and-memory.md` |
| Language and Style | Documentation languages, communication register, author voice, cognitive bias checks | `FISS/overrides/style.md` |

### Example: Overriding Open Questions Lifecycle

A skill's built-in default may allow a `Deferred` status. If the project does not allow deferring open questions when they can be resolved immediately, the rule should be defined in `FISS/overrides/skills/open-questions.md`:

```markdown
# Open Questions

## Lifecycle

Status describes the state of knowledge, not the state of workflow:

- `Active` — uncertainty exists and remains significant; investigation or dependency does not change this status.
- `Needs review` — evidence indicates context change or violation of a "Review if" condition; unknown freshness or evidence conflict alone does not change status.
- `Resolved` — sufficient justification exists to consider the question resolved, with "Resolved via" specified; this is an outcome of resolution, not an active tracking status.
- `Superseded` — question is subsumed by another question or decision; link to replacement in resolution history.
- `Withdrawn` — original formulation is invalid or no longer has basis; record rationale in resolution history.

Do not introduce separate `Investigating` and `Blocked` statuses: a question under study or awaiting dependency remains `Active`, with dependencies noted in context. Do not use `Deferred`: the project does not permit deferring open questions.

In active record templates, only `Active` and `Needs review` are permitted. The "Why deferred" field is omitted; transition to `Deferred` is removed from reconciliation procedures. Waiting on research or dependencies is not grounds for resolving a question.
```

This document does not modify the skill itself. It clarifies how the skill must be applied in this specific project, explaining the rationale for divergence from default behavior.

### Operational Artifacts and Portability

A skill working with an operational artifact must not assume its specific location.

For example, a skill may operate on a task plan and set a specific filename for it, such as `plan.md`, but must not assume that this file is always located in:

```text
_currenttask/plan.md
```

We can define a common directory for all operational artifacts, for example in `FISS/overrides/artifacts.md` like this:

```md
# Skills

All operational artifacts in the project are stored in the `_currenttask/` directory.
```

If it is necessary to change the artifact's filename (when it is specified inside the skill as `plan.md`), this is an override of skill behavior, which can be configured in `FISS/overrides/skills/writing-plans.md` like this:

```md
# Paths

The operational artifact of the current task plan must be located at `_currenttask/task-plan.md`
```
