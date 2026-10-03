> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/intellectual-space) · 🇷🇺 [Русская версия](ru/intellectual-space.md)

---

## Intellectual Space

An intellectual space is an abstract logical space that supports collaboration between people and AI agents. It describes knowledge, rules, state, context, and artifacts by their purpose and relationships rather than by their storage technology.

FISS is the filesystem-based standard that realizes this model.

### Logical Model

An intellectual space contains logical artifacts. A logical artifact is identified by its purpose, not by a path or format. It may represent knowledge, a rule, current state, a decision, a plan, evidence, or another project concern.

Artifacts may relate to one another. The space should make those relationships understandable and should help a person or agent determine which context applies to a particular task.

Knowledge is canonical by default. It is derived only when explicitly marked with the exact, non-localized marker `Derived from:` and linked to its source or sources. The same knowledge must not be maintained independently in multiple places: one representation remains canonical and every other representation is derived.

An external mechanism is a mechanism used by the intellectual space but not part of the project or its intellectual space. Skills, task trackers, documentation systems, version-control systems, tools, and processes are examples. External mechanisms remain independent, while project rules may override how they are applied without modifying the mechanisms themselves.

### Principles

**ZLOC** (**Z**ero **L**oose, zero **O**verhead **C**ontext) — do not lose useful context or create unnecessary context.

ZLOC defines the overall goal of an intellectual space. The seven 7C principles describe its organization and maintenance:

1. <a id="principle-compact"></a>**Start small.** (Compact) Expand the space when new information or context is needed.

2. <a id="principle-context-aware"></a>**Make applicability visible.** (Context-aware) Organize information so that it is possible to determine when it is needed.

3. <a id="principle-context-first"></a>**Separate navigation from content.** (Context-first) Navigation selects context, while detailed knowledge and rules reside in content artifacts.

4. <a id="principle-classified"></a>**Distinguish information classes.** (Classified) Durable knowledge, current state, and rules for changing state serve different purposes.

5. <a id="principle-canonical"></a>**Keep canonical sources clear.** (Canonical) Copies, summaries, and projections MUST NOT silently become competing sources of truth.

6. <a id="principle-continuous"></a>**Maintain context.** (Continuous) Timely capture useful changes to the project's context.

7. <a id="principle-composable"></a>**Keep external mechanisms independent.** (Composable) Project rules MAY adapt how they are applied without incorporating their storage, lifecycle, or implementation into the space.

Other standards may realize the intellectual-space model using databases, APIs, data lakes, or other mechanisms. FISS defines its filesystem realization in the remaining documentation.
