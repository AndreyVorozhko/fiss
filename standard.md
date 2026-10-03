> 📖 [Table of Contents](README.md) · 🛠️ [FISS Linter](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Original Normative Source: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/en/standard) · 🇷🇺 [Русская версия](ru/standard.md)

---

## Referencing the Standard

In `FISS/INDEX.md`, it is recommended to include a link to the standard and the edition in use. For maximum resilience, it is recommended to provide both the primary link to the official standard website (`https://fiss.vorozhko.ru`) and a fallback link to its official Git repository mirror on GitHub: [`https://github.com/AndreyVorozhko/fiss`](https://github.com/AndreyVorozhko/fiss) for scenarios when the site is unavailable or work is conducted in an offline environment.

For the edition in use, provide a permanent link to its specific version or page (for example, the versioned AI context `https://fiss.vorozhko.ru/v1.0.0/llms.txt` or the version branch on the GitHub mirror `https://github.com/AndreyVorozhko/fiss/blob/v1.0.0/llms.txt`).

Recommended example of providing both links in `FISS/INDEX.md`:

```markdown
- [File-based Intellectual Space Standard](https://fiss.vorozhko.ru/v1.0.0/llms.txt)
  Read when: creating or modifying the intellectual space structure or verifying conformance.
- [File-based Intellectual Space Standard (GitHub Mirror)](https://github.com/AndreyVorozhko/fiss/blob/v1.0.0/llms.txt)
  Read when: https://fiss.vorozhko.ru is unavailable or working in an offline environment.
```

Automated validation tools (such as rule `FISS-R011` in `fiss-lint`) accept either link individually as well as having both links present.

Reading the entire standard before each task is not required.
