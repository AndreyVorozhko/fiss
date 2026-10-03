# File-based Intellectual Space Standard (FISS)

> **Version v1.0.0** · Minimal filesystem-based intellectual space organization and navigation model for seamless human-AI collaboration.
>
> 🌐 **Canonical Website & Interactive Documentation:** [https://fiss.vorozhko.ru](https://fiss.vorozhko.ru)  
> 🇷🇺 **Русская версия:** [Документация на русском языке](ru/README.md)  
> 🛠️ **FISS Linter:** [github.com/AndreyVorozhko/fiss-lint](https://github.com/AndreyVorozhko/fiss-lint)  
> 🧠 **FISS Skills:** [github.com/AndreyVorozhko/fiss-skills](https://github.com/AndreyVorozhko/fiss-skills)  
> 🤖 **Machine Context (LLM):** [llms.txt](llms.txt) · [llms-full.txt](llms-full.txt)

---

## Overview

**Intellectual space** is the logical system of project knowledge, rules, state, context, and artifacts that supports collaboration between humans and AI agents. It is independent of storage technology.

In practice, its foundation can be organized as a `FISS/` directory in the project root. Within this directory, the team maintains useful context and links to other sources: code, documentation, task trackers, and tools.

**FISS (File-based Intellectual Space Standard)** is the filesystem-based realization of the intellectual-space model. It describes how to organize the `FISS/` directory so that a team member or AI agent can locate needed information and determine when it is applicable context for work.

The standard defines organization and navigation; the project team defines the content. FISS does not prescribe product architecture, development methodology, toolchains, lifecycles, or project documents beyond two required root files.

### Key Features
- **File-Based Structure**: Self-contained, portable, and transparent filesystem layout.
- **Strict Versioning (v1.0.0)**: Frozen release tagged in Git.
- **Machine Representations**: [`llms.txt`](llms.txt) (normative specification 1:1) and [`llms-full.txt`](llms-full.txt) (complete documentation context) ready for AI agents.

---

## Documentation (Table of Contents)

- [Introduction](index.md)
- [Intellectual Space](intellectual-space.md)
- [Standard Boundaries and Scope](limits.md)
- [Quick Start](start.md)
- [Referencing the Standard](standard.md)
- [Navigation Model](navigation.md)
- [Information Areas](areas.md)
- [Maintaining the Intellectual Space](maintenance.md)
- [Canonical Sources, Links, and History](sources.md)
- [FISS and Agent Skills](skills.md)
- [Conformance Checklist](conformance.md)
- [FISS Tool Ecosystem](ecosystem.md)
- [Examples](examples.md)

---

## Tools & Ecosystem

- **[FISS Linter](https://github.com/AndreyVorozhko/fiss-lint)**: Static analysis and conformance verification tool for FISS intellectual spaces.
- **[FISS Skills](https://github.com/AndreyVorozhko/fiss-skills)**: Specialized agent skills (e.g., `fiss-maintain`, `fiss-validate`) for managing and validating FISS intellectual spaces.

---

## Machine Representations for AI Agents

- **[llms.txt](llms.txt)**: Normative core specification 1:1 in clean text format.
- **[llms-full.txt](llms-full.txt)**: Complete human documentation combined into a single file for AI context windows.

---

## Original Source & Mirror Status

This repository is an offline Git mirror of the **File-based Intellectual Space Standard (v1.0.0)**.  
The original normative source and full web edition is published at **[https://fiss.vorozhko.ru](https://fiss.vorozhko.ru)**.

License: [MIT License](LICENSE)
