> 📖 [Оглавление](README.md) · 🛠️ [Линтер FISS](https://github.com/AndreyVorozhko/fiss-lint) · 🌐 [Оригинальный нормативный источник: fiss.vorozhko.ru](https://fiss.vorozhko.ru/v1.0.0/ru/standard) · 🇬🇧 [English version](../standard.md)

---

## Ссылка на используемый стандарт

В `FISS/INDEX.md` рекомендуется указывать ссылку на стандарт и используемую редакцию. Для максимальной надёжности и устойчивости к сбоям рекомендуется указывать сразу две ссылки: на официальный сайт стандарта (`https://fiss.vorozhko.ru`) и на его официальное Git-зеркало на GitHub: [`https://github.com/AndreyVorozhko/fiss`](https://github.com/AndreyVorozhko/fiss) в качестве резервного источника на случай недоступности сайта или работы в автономном окружении.

Для используемой редакции рекомендуется давать постоянную ссылку на конкретную версию (например, страницу версии, машинный контекст `https://fiss.vorozhko.ru/v1.0.0/llms.txt` или зеркало на GitHub `https://github.com/AndreyVorozhko/fiss`).

Рекомендуемый пример указания обеих ссылок в `FISS/INDEX.md`:

```markdown
- [File-based Intellectual Space Standard](https://fiss.vorozhko.ru/v1.0.0/llms.txt)
  Read when: создаётся или изменяется структура интеллектуального пространства либо проверяется соответствие стандарту.
- [File-based Intellectual Space Standard (GitHub Mirror)](https://github.com/AndreyVorozhko/fiss)
  Read when: недоступен https://fiss.vorozhko.ru или работа ведётся в автономном окружении.
```

Инструменты автоматической проверки и статического анализа (например, правило `FISS-R011` в линтере `fiss-lint`) засчитывают как наличие любой из этих ссылок, так и их совместное указание.

Читать весь стандарт перед каждой задачей не требуется.
