# IdkRx Skills

Public skills for the [IdkRx API](https://idkrx.com) — pharmacy search, medication data, and shortage tracking. Each skill is a `SKILL.md` file with endpoint references, parameters, and runnable examples that teach LLMs and developers how to use the IdkRx API surface.

## Install

```bash
npx skills add idkrx/skills
```

Or install a specific skill:

```bash
npx skills add idkrx/skills --skill local-demo-testing
```

## Skills

| Skill | Description |
|---|---|
| [local-demo-testing](./skills/local-demo-testing/SKILL.md) | Example skill for testing installation and learning the IdkRx API surface |

## Structure

Skills follow the [Agent Skills specification](https://agentskills.io/specification). Each skill is a directory under `skills/` containing:

```
skills/<skill-name>/
├── SKILL.md          # Required: metadata + instructions
├── scripts/          # Optional: executable code
├── references/       # Optional: documentation
└── assets/           # Optional: templates, resources
```

## Creating a Skill

Copy the [template](./template/SKILL.md) and fill in your skill's instructions:

```yaml
---
name: my-skill
description: A clear description of what this skill does and when to use it
metadata:
  version: "0.1.0"
  author: idkrx
---

# my-skill

Instructions for LLMs and developers on how to use the IdkRx API for this task.
```

## Docs

Full documentation at [docs.idkrx.com/skills](https://docs.idkrx.com/skills).

## License

MIT
