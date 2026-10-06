# Skill Index

This document provides an index of all available skills in this repository for the Antigravity AI coding assistant.

Each skill lives in its own directory containing a `SKILL.md` instruction file with frontmatter metadata.

---

## Skills Overview

| Skill | Slash Command / Trigger | Description | Version |
| :--- | :--- | :--- | :--- |
| [`released-bump`](./released-bump/SKILL.md) | `/release-bump`, `/released-bump`, `/release` | Bump version, generate release notes from rules, create Git tag, and publish GitHub release with export folder artifacts | `1.0.0` |
| [`workspace-allow`](./workspace-allow/SKILL.md) | Autonomous / Boundary | Enforces full agent autonomy within workspace directory while requiring explicit confirmation for external paths | `1.0.0` |

---

## Detailed Skill Listing

### 1. [Release & Version Bump Automation (`released-bump`)](./released-bump/SKILL.md)
- **Directory**: [`released-bump/`](./released-bump/)
- **Instruction File**: [`released-bump/SKILL.md`](./released-bump/SKILL.md)
- **Slash Commands**: `/release-bump`, `/released-bump`, `/release`
- **Description**: Automates end-to-end version bumping, reading project rules to generate `RELEASED_NOTE/{version}.md`, creating annotated Git tags, and publishing a GitHub release via `gh release create` with attached artifacts from the target export folder.
- **Key Guidelines & Capabilities**:
  - **Version Detection**: Detects and bumps SemVer (`patch`, `minor`, `major`) in `VERSION`, `package.json`, `Cargo.toml`, `pyproject.toml`, or `deno.json`. Defaults to `patch`.
  - **Rule-Driven Release Notes**: Reads project rules (e.g., `rules/release-note.md` or `.agents/rules/release-note.md`) and generates `RELEASED_NOTE/{version}.md` containing categorized commit history (`Added`, `Changed`, `Fixed`, `Removed`).
  - **Export Verification**: Verifies presence of built artifacts in `--export <dir>` or standard output directories (`export/`, `dist/`, `build/`, `out/`, `release/`), triggering the project build step if empty.
  - **Git Operations**: Commits release files (`chore(release): v{version}`), creates annotated tag `v{version}`, and pushes both commit and tag upstream.
  - **GitHub Release**: Creates the release on GitHub via `gh release create` attaching all export folder assets and linking the release note.

### 2. [Scoped Directory Operations & Workspace Boundary Enforcement (`workspace-allow`)](./workspace-allow/SKILL.md)
- **Directory**: [`workspace-allow/`](./workspace-allow/)
- **Instruction File**: [`workspace-allow/SKILL.md`](./workspace-allow/SKILL.md)
- **Trigger**: Continuous / Scoped Boundary
- **Description**: Grants full agent autonomy inside the designated workspace directory while enforcing explicit user confirmation for actions targeting external paths or system commands outside the repository sandbox.
- **Key Guidelines & Capabilities**:
  - **In-Scope Autonomy**: Allows editing, reading, deleting, and building within `./` without prompting for confirmation.
  - **Out-of-Scope Protection**: Halts and prompts with a structured confirmation warning if an action references absolute paths outside the repo, parent directory traversals (`../`), or global package managers.

---

For installation methods and contributing guidelines, see [README.md](./README.md).
