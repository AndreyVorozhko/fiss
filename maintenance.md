> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/maintenance) · 🇷🇺 [Русская версия](ru/maintenance.md)

---

## Maintaining the Intellectual Space

### Current Task and Outcomes

Operational task materials may be kept in a designated task workspace, such as `_currenttask/` outside `FISS/`. This workspace can house task statements, research, plans, and intermediate artifacts, including operational artifacts described in the skills section. It serves as an active workspace for the task; its organization is defined by the team. Being located outside `FISS/` does not exclude these materials from the broader intellectual space of the project.

If a project uses such a workspace, document its rules in an appropriate project document: for example, in `FISS/knowledge/project/` or in `FISS/overrides/` if overriding skill defaults.

Workflow documentation should specify applicable project rules:

- Which materials are temporary and what happens to them upon task completion;
- What results must be transferred into durable knowledge and when;
- Where task state is tracked;
- Which files are committed to version control and which are excluded.

It can also describe how logical artifacts used by skills map to project files or external systems.

Thus, FISS accommodates both long-term knowledge and immediate state. Workflow rules tie them directly to ongoing team work.

### Updating Materials

The context applicability condition (`Read when`) declared in navigation serves as a natural guide for maintenance: if a task operated within the situation described by that condition and produced a FISS-relevant outcome by modifying domain rules, architecture, decisions, or project state, the materials describing them must be brought into alignment with the new reality. Operational work that uses the intellectual space as context without changing what it represents produces no FISS-relevant outcomes and requires no updates. Updating a document requires no separate modification marker — it is the direct consequence of producing a FISS-relevant outcome within the applicable context.

To realize the [“Maintain context” principle](./intellectual-space.md#principle-continuous), it is recommended to incorporate a context audit into the standard task completion checklist:

* Did valuable new knowledge emerge that benefits subsequent tasks? Transfer it to the appropriate area or primary external source.
* Did rules, architectural decisions, constraints, or active state change? Update the affected documents.
* Were files added, moved, or renamed? Update indexes, read conditions, and incoming links.
* Did a canonical source change? Review related materials marked `Derived from:` and update or deprecate them as needed.

In practice, this check is conveniently performed as part of task completion: review the work outcomes and determine whether they are FISS-relevant. FISS-relevant outcomes should be **preserved**, **handed off to the owner of the respective material**, or **explicitly classified** as not requiring persistence. Operational work that uses the intellectual space as context without changing what it represents produces no FISS-relevant outcomes and requires no integration. For example, a FISS maintenance skill can be created to classify outcomes in this way after each task and **consider work complete only after integrating** all FISS-relevant outcomes into the relevant sections of the intellectual space. For an individual developer, this may mean that after completing a task that produced FISS-relevant outcomes, they should ensure those outcomes are integrated into FISS before starting different independent work.

In parallel work, this does not require waiting for other tasks to complete: if a task depends on an outcome that is not yet integrated into FISS, that outcome should be explicitly included in its working context. Once the dependent work is complete, the outcome should be integrated into FISS in the regular manner.

This is the recommended maintenance workflow; specific roles and review moments are determined by the team.
