# research_harness

A plug-and-play harness for running research projects with AI agents (Claude Code, Codex, or any
agent that reads `AGENTS.md`). Agents do research, outlines, pushback and feedback loops; you write
the final prose. Rigour scales from coursework to doctoral/journal work (`AGENTS.md` §0.6).

## What is tracked
| File | Purpose |
|---|---|
| `AGENTS.md` | Operating manual: bootstrap protocol, integrity rules, quality gates, Knowledge Base, playbooks |
| `CLAUDE.md` | Makes Claude Code load `AGENTS.md` |
| `templates/` | Profile, progress, project requirements, references, review matrix, AI-use log, pushback memo, pre-analysis plan, data README |
| `CHANGELOG.md` | Harness changes |

Everything else (your profile, projects, course materials, data) is git-ignored by a whitelist
`.gitignore`, so personal and copyrighted material never leaves your machine.

## Quick start
1. Clone the repo and open it with your agent.
2. Copy `templates/PROFILE.md` → `PROFILE.md` and fill in your details and your institution's AI-use policy.
3. Copy `templates/ROOT_PROGRESS.md` → `PROGRESS.md`.
4. Put course or reference materials in a local folder (e.g. `Course/`) and list it in `PROFILE.md` §4.
5. Ask the agent to start a project, e.g. *"New project P1: <brief>"*. It creates
   `P1/AGENTS.md` and `P1/PROGRESS.md` from the templates and shows you the plan before working.

Every later session starts the same way: the agent reads `AGENTS.md`, `PROFILE.md`, `PROGRESS.md`
and the project's files, restates the current step, and works on that step only.

## Versioning a project
Projects are ignored here. To version one, run `git init` inside its folder and push it to a
**private** repository.
