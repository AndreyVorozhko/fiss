> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/sources) · 🇷🇺 [Русская версия](ru/sources.md)

---

## Canonical Sources, Links, and History

### Avoiding Contradictions

A **canonical source (source of truth)** is the authoritative location for particular knowledge or a class of information. Knowledge in FISS is canonical by default: if material does not contain `Derived from:`, it is a canonical source for the knowledge it contains. Canonicality is not assigned by directory or area.

Projects may designate authoritative external sources or precedence rules for information classes. For example:

| Information Class | Potential Canonical Source |
| --- | --- |
| Task status | Issue tracker |
| Architecture decisions | ADR repository |
| Project conventions | Relevant documents in `FISS/knowledge/` |
| File change history | Version-control system |

This illustrates separation of responsibilities rather than a fixed FISS hierarchy. Project rules should be placed where they will be encountered when working in that context; broad rules belong in `FISS/BOOTSTRAP.md`.

In accordance with the [“Keep canonical sources clear” principle](./intellectual-space.md#principle-canonical), the same knowledge MUST NOT be maintained independently in multiple places. If a copy, summary, map, diagram, or other representation is useful, exactly one representation remains canonical and every other one must be explicitly derived.

The only derivation marker is the exact English text `Derived from:`. It is never localized and must be followed by Markdown links leading directly to the source materials. Include every material source needed to understand the representation's origin and verify it:

```markdown
Derived from:
- [Project architecture](../../knowledge/project/architecture.md)
- [Payment domain](../../knowledge/subject/payment.md)
```

This rule concerns duplicated knowledge, not matching fragments of text or useful differences in representation. A concise architecture diagram and a detailed description can coexist when the diagram identifies the description and any other material sources through `Derived from:`. Derived knowledge does not become canonical merely by existing, and it should be reviewed when its sources change.

When sources conflict, do not silently pick a preferred version. Apply the designated source rule. If no rule exists, resolving the conflict requires an explicit team decision.

### Linking Materials

Relationships between artifacts are expressed with standard Markdown links and concise explanations. A formal typed relationship syntax is not required.

For example, in `FISS/state/adr/payment-decision.md`:

```markdown
This decision resolves [the open question on payment models](../../state/open-questions/payment-model.md).
```

The two-line format with an explicit read condition marker (`Read when:`) is required for navigation links in indexes. In substantive documents, a brief explanatory note describing the relationship is sufficient.

### When In-Document History is Needed

Change logs inside individual documents are optional. For files under Git version control, technical revision history is already tracked by the repository.

Status or changelog notes are valuable when their omission could lead to misapplying the material. For instance, a decision record can indicate whether it is active, superseded, or withdrawn, with a link to its successor. The team determines whether individual documents require internal changelogs.
