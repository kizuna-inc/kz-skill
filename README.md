# kz-skill

A collection of Coding agent skills maintained by **Kizuna Inc.**

Skills are plug-in instruction sets for the Antigravity AI coding assistant. Each skill lives in its own directory and contains a `SKILL.md` file that Antigravity reads to extend its behaviour for a specific domain.

---

## Available Skills

| Skill | Slash Command / Trigger | Description | Version |
| :--- | :--- | :--- | :--- |
| [`released-bump`](./released-bump/SKILL.md) | `/release-bump`, `/released-bump`, `/release` | Bump version, generate release notes from rules, create Git tag, and publish GitHub release with export folder artifacts | `1.0.0` |
| [`workspace-allow`](./workspace-allow/SKILL.md) | Autonomous / Boundary | Enforces full agent autonomy within workspace directory while requiring explicit confirmation for external paths | `1.0.0` |
| [`auto-mode`](./auto-mode/SKILL.md) | `/auto-mode` | Enables auto mode for antigravity tool, allowing automatic execution without interactive prompts. | `1.0.0` |

For the complete list and detailed documentation of all available skills, see the [Skill Index](skill_index.md).

All individual skills live in their own directory containing a `SKILL.md` runbook.

---

## Usage

### Installing a skill globally (all projects on your machine)

Copy the skill directory into your Antigravity global config folder:

```bash
cp -r <skill-name> ~/.gemini/config/skills/
```

Skills placed here are automatically discovered and available in every project on your machine.

### Installing a skill per-project (shared with your team)

Copy the skill directory into a `.agents/skills/` folder at the root of your project and commit it:

```bash
mkdir -p .agents/skills
cp -r <skill-name> .agents/skills/
```

Antigravity walks from your working directory up to the repo root, loading all skills it finds under `.agents/` (also recognised as `.agent/`, `_agents/`, `_agent/`). Checking this folder into version control shares the skill with your whole team.

> **Priority:** Project-level skills (`.agents/`) take precedence over global ones (`~/.gemini/config/`), which in turn take precedence over built-in defaults.

---

## Contributing

1. Fork this repo and create a new branch.
2. Add your skill as a new directory (e.g. `my-new-skill/SKILL.md`).
3. Follow the Antigravity skill format — include `name`, `author`, `description`, `license`, `version`, and `tags` in the YAML front-matter of `SKILL.md`.
4. Add the new skill entry to the [Skill Index](skill_index.md).
5. Open a pull request with a short description of what the skill enforces or enables.

---

## License

MIT © [Kizuna Inc.](https://github.com/kizuna-inc)
