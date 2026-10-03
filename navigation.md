> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/navigation) · 🇷🇺 [Русская версия](ru/navigation.md)

---

## Navigation Model

### Indexes Determine Context Applicability

`FISS/INDEX.md` is the primary entry point. Indexes of individual areas are also named `INDEX.md` and reside within corresponding directories.

The core mission of an index is to answer: **"when is this material applicable context for work?"**, rather than trying to predict low-level filesystem operations (such as reading versus modifying a file).

The `Read when:` marker designates a **context applicability condition** (entry into working context). It is not merely a mechanical command to open a file; it specifies the situational trigger under which the material must be loaded into the working context of a person or AI agent.

Every navigation entry in an index file follows a strict three-element pipeline:

```text
navigation link
    ↓
reading condition marker (applicability marker)
    ↓
non-empty condition (situational trigger)
```

The standard establishes a **strict two-line format** for every navigation link:
1. First line — Markdown link to the target document or index: `- [Title](target)`
2. Second line — An attached line indented by 2 spaces containing an explicit read condition marker and a non-empty condition: `  Read when: condition`

The read condition marker MUST always be the English text `Read when:`. It MUST NOT be localized or translated into other languages. This ensures deterministic parsing by automated tools and linters (such as `fiss-lint`) without the overhead or ambiguity of language detection.

Example root index for a project with multiple areas:

```markdown
# Project Intellectual Space

- [Baseline Context](BOOTSTRAP.md)
  Read when: beginning work on the project or onboarding to the space.
- [Domain Knowledge](knowledge/subject/INDEX.md)
  Read when: modifying business rules or working with domain concepts.
- [Project Architecture](knowledge/project/architecture.md)
  Read when: modifying system components or configuring the environment.
- [Current State](state/INDEX.md)
  Read when: risks, open questions, or temporary constraints may affect the task.
```

### Context Entry and Why There Is No “Modify when”

A natural question may arise: if we not only read files but also modify them, shouldn't there be a symmetric marker like `Modify when:`?

In FISS, there is **intentionally no `Modify when` marker**, and it should not be introduced for fundamental architectural reasons:

1. **`Read when` defines entry into context, not a filesystem operation.** The index defines under what conditions the material becomes part of the task's working context.
2. **Modifying a file is a natural consequence of working in that context.** If an agent or engineer is modifying project architecture, they must consult the material describing architecture (`Read when: modifying system components...`), and upon completing the change, update it to align with the new reality.
3. **FISS does not manage file lifecycles.** The standard defines intellectual space organization and navigation, leaving lifecycles and processes to the project. Introducing `Modify when` would turn navigation into a file lifecycle management language and overburden navigation syntax with redundant markers.

The context operational model is straightforward:

```text
INDEX
  ↓
Read when (determines applicable context)
  ↓
agent or engineer reviews the material
  ↓
works with it / utilizes context in the task
  ↓
if work altered what the material describes
  ↓
material is updated to reflect the outcome
```

The index answers: **"when is this material needed?"**, without trying to anticipate what specific operations the agent will perform after opening the document.

### Eliminating Ambiguity

A frequent anti-pattern in loose documentation is formatting links as passive annotations or pointing directly to bare directories:

```markdown
- [Project Knowledge](knowledge/project/) - Contains project knowledge.
```

This violates the standard on multiple counts:
1. **Targeting a bare directory**: A navigation link MUST target a specific file (`.md`) or an area's `INDEX.md`, not an untyped filesystem directory.
2. **Missing marker**: The required read condition marker (`Read when:`) is absent.
3. **Passive description instead of condition**: The phrase "Contains project knowledge" states what is stored inside, rather than explaining the situational trigger — the working situation where a person or agent must load that context.
4. **Single-line format**: The read condition MUST reside on a separate line indented by 2 spaces.

The label "Domain Knowledge" only describes content. The read condition "Read when: modifying business rules..." helps determine whether the material is applicable context for the current task — this implements the [“Make applicability visible” principle](./intellectual-space.md#principle-context-aware).

Enforcing a strict two-line format and an explicit marker makes navigation deterministic and reliably verifiable: automated linters (e.g., `fiss-lint`) and validation skills (`fiss-validate`) can unambiguously check navigation integrity without heuristic guesswork.

Following the [“Separate navigation from content” principle](./intellectual-space.md#principle-context-first), an index must remain concise: links, context applicability conditions, and necessary navigational notes. Detailed content belongs in the referenced documents. This enables moving from general context to specifics on demand.

### An Area Can Be a File or a Directory

An **area** is a thematically coherent unit in an intellectual space, such as project knowledge or open questions.

| Form | When to Use | Naming Rule |
| --- | --- | --- |
| Single file | The topic fits in one document | The filename is determined by the project |
| Directory with `INDEX.md` — composite area | The topic spans multiple documents | `INDEX.md` serves as the entry point |
| Directory without `INDEX.md` — container | Groups related areas together | Links to child areas reside in the enclosing index |

For example, `FISS/knowledge/` can serve as a container:

```text
FISS/
├── INDEX.md
├── BOOTSTRAP.md
└── knowledge/
    ├── project/
    │   └── architecture.md
    └── subject/
        ├── INDEX.md
        ├── access.md
        └── notifications.md
```

In this example, the root index links to `FISS/knowledge/project/architecture.md` and `FISS/knowledge/subject/INDEX.md`. The index `FISS/knowledge/subject/INDEX.md` navigates its area materials. A separate `FISS/knowledge/INDEX.md` is not required.

Filenames of single-file areas and other substantive documents, like `access.md`, are determined by the project. The standard reserves the names `INDEX.md` for navigation points and `BOOTSTRAP.md` for the required baseline context.

All used areas must be reachable through navigation from `FISS/INDEX.md`. The index of a composite area must navigate to its materials and child areas; through a container, links point directly to nested areas. Every index link must adhere to the strict two-line format with a read condition marker.

### Expanding an Area

When a single file outgrows its scope, it can be replaced with a directory containing an index:

```text
Before:                     After:
FISS/state/                 FISS/state/
└── open-questions.md        └── open-questions/
                                ├── INDEX.md
                                ├── payment-model.md
                                └── access-policy.md
```

When making this transition, update all incoming links. The new `INDEX.md` follows the same navigation rules as the root index.

### Structure for Future Decomposition

In single-file areas, it is recommended to design a modular structure from the outset that can easily be divided into separate files as the document grows. This helps adhere to the [“Start small” principle](./intellectual-space.md#principle-compact): starting with a simple single file while proactively preventing friction during future decomposition.

When the material within a file is organized into logically self-contained sections and subsections, each section becomes a natural candidate for extraction into a separate document or child area without having to untangle or rewrite intertwined text.

For example, an initial `FISS/knowledge/project/architecture.md` might contain:

```markdown
# Frontend

## General Rules

- In `admin` and `front`, use TypeScript, not JavaScript.
- In TypeScript, do not use trailing semicolons `;`.
- Do not duplicate types between pages.
- Prefer a composable-first approach for backend interactions.

## Admin

- `admin` — Nuxt 4 SPA + `naive-ui`; SSR is disabled.
- `admin` SPA serves two hosts: admin host for `/admin` and business host for `/business`; do not add cross-host redirects that expose the admin host to business users.
- Use `admin/app/utils/apiFetch.ts` for backend requests, never direct `fetch`.

# Cache

## Redis Clients and DB Partitioning

- Redis is partitioned by responsibility:
  - DB0 / `snc_redis.token_store` / prefix `token:` — only refresh-token whitelist and auth/token storage.
  - DB1 / `snc_redis.app_cache` / prefix `cache:` — only application cache.
- Do not store application cache in DB0.
- Do not store auth/session/token data in DB1.
- Cache is not a source of truth. PostgreSQL and domain services remain authoritative.

## Application Cache Rules

- Every application cache entry must have an explicit TTL.
- Cache key must account for all request parameters and context values that can alter the response.
- Cache key must be deterministic and stable for equivalent requests.
- Never include raw user input, tokens, cookies, secrets, raw personal data, full URL with query strings, or request bodies in cache keys.
- If user input is unavoidable in a cache key in the future, normalize it first and prefer a safe hash/fingerprint over raw values.
- When adding or modifying a cache, specify an invalidation strategy in the same task.
- If invalidation is coarse-grained, document this explicitly and keep the TTL conservative.
```

When this file grows large, its clean modular structure allows it to be naturally split into, for example:

- `FISS/knowledge/project/frontend/common-rules.md`
- `FISS/knowledge/project/frontend/admin.md`
- `FISS/knowledge/project/cache.md` (or `FISS/knowledge/project/cache/INDEX.md`)
