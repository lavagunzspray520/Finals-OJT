# Agent Guide

This file tells AI coding agents (Kiro, Codex, Cursor, Claude, etc.) how to work
effectively in this repository. Keep it short, specific, and up to date.

## Project Overview

- **Name:** Finals-OJT
- **Purpose:** Final On-the-Job Training (OJT) deliverables and documentation.
- **Owner:** lavagunzspray520
- **Status:** Work in progress

## Repository Structure

```
Finals-OJT/
├── README.md      # Project overview
├── agent.md       # This file - guidance for AI agents
└── skills.md      # OJT skills, technologies, and progress log
```

> Update this tree whenever new top-level folders or files are added.

## Tech Stack

- _Fill in as the project grows_ (e.g., language, framework, database, deployment target).

## Setup

```bash
# Clone the repo
git clone https://github.com/lavagunzspray520/Finals-OJT.git
cd Finals-OJT

# Install dependencies (update once a stack is chosen)
# e.g. npm install  /  pip install -r requirements.txt
```

## Common Commands

| Task          | Command                       |
|---------------|-------------------------------|
| Install deps  | _TBD_                         |
| Run locally   | _TBD_                         |
| Run tests     | _TBD_                         |
| Lint / format | _TBD_                         |
| Build         | _TBD_                         |

## Coding Conventions

- Use clear, descriptive names for files, functions, and variables.
- Keep functions small and focused on one responsibility.
- Prefer readability over cleverness.
- Add comments only where intent is non-obvious.

## Git Workflow

- `main` is the protected default branch — do **not** commit directly to it.
- Create a feature branch: `git checkout -b feature/<short-name>`.
- Commit messages: short imperative subject, e.g. `Add login form validation`.
- Open a Pull Request and request review before merging.

## Instructions for AI Agents

When working in this repo, agents should:

1. **Read `README.md`, `agent.md`, and `skills.md` first** to gather context.
2. **Never push directly to `main`.** Always use a new branch and a pull request.
3. **Keep changes scoped.** Don't refactor unrelated code in the same PR.
4. **Update documentation** (`README.md`, `agent.md`, `skills.md`) when behavior or structure changes.
5. **Ask before destructive operations** (force-push, history rewrite, deleting files).
6. **Match existing code style** — if a convention exists, follow it.

## Out of Scope

- Production credentials, secrets, or `.env` files must never be committed.
- Do not add large binary assets without discussion.

## Contact

- Repository owner: [@lavagunzspray520](https://github.com/lavagunzspray520)
