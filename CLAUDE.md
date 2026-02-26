# CLAUDE.md — AI Assistant Guidelines for CC

This file provides context, conventions, and workflow instructions for AI assistants (such as Claude Code) working in this repository.

---

## Repository Overview

| Property       | Value                          |
|----------------|-------------------------------|
| **Repo name**  | CC                             |
| **Owner**      | Ubermensch-6920                |
| **Remote**     | http://local_proxy@127.0.0.1:57049/git/Ubermensch-6920/CC |
| **Default branch** | `master`                   |
| **Status**     | Early-stage / initializing     |

This repository currently contains only a placeholder `README.md`. Its tech stack, language, and full structure are to be determined as the project evolves. This CLAUDE.md should be updated whenever significant structure or conventions are established.

---

## Current File Structure

```
CC/
├── README.md      # Project title placeholder ("# CC")
└── CLAUDE.md      # This file
```

---

## Git Workflow

### Branch Naming

Feature branches created by AI assistants must follow the pattern:

```
claude/<task-slug>-<session-id>
```

Example: `claude/claude-md-mm3nt85bboba17pm-JOzgS`

- Always develop on the designated branch, never directly on `master`.
- Create the branch locally if it does not already exist.

### Push Protocol

Always use the `-u` flag to set upstream tracking:

```bash
git push -u origin <branch-name>
```

If the push fails due to network errors, retry with exponential backoff:
- Wait 2s, retry
- Wait 4s, retry
- Wait 8s, retry
- Wait 16s, retry (final attempt)

Do **not** retry on non-network errors (e.g., HTTP 403 — check the branch name is correct).

### Fetch / Pull

Prefer fetching specific branches over full fetches:

```bash
git fetch origin <branch-name>
git pull origin <branch-name>
```

Apply the same exponential backoff retry policy for network failures.

### Commit Messages

Write clear, imperative-style commit messages:

```
Add CLAUDE.md with repository guidelines
Fix authentication bug in login flow
Update README with setup instructions
```

- First line: short summary (≤72 chars), imperative mood
- Leave a blank line before the body if additional detail is needed
- Reference issue/PR numbers where applicable

---

## Development Conventions (to be filled as project grows)

Since the project is in its initialization phase, conventions are not yet established. As code is added, update this section to capture:

- **Language & runtime**: (e.g., Node 20, Python 3.12, Go 1.22)
- **Package manager**: (e.g., npm, pnpm, pip, cargo)
- **Linter / formatter**: (e.g., ESLint + Prettier, Ruff, gofmt)
- **Test framework**: (e.g., Jest, pytest, Go test)
- **Build system**: (e.g., Vite, tsc, Makefile)

---

## AI Assistant Instructions

### General Principles

1. **Read before editing.** Always read a file before modifying it. Understand existing code before suggesting changes.
2. **Minimal changes.** Only make changes that are directly requested or clearly necessary. Do not refactor, add docstrings, or "clean up" surrounding code unless asked.
3. **No guessing URLs.** Never fabricate URLs. Only use URLs provided by the user or found in local files.
4. **Security first.** Never introduce SQL injection, XSS, command injection, or other OWASP Top 10 vulnerabilities. Fix security issues immediately if discovered.
5. **No over-engineering.** Keep solutions simple. Avoid premature abstractions, unnecessary helpers, or hypothetical future-proofing.

### File Operations

- Use dedicated tools (Read, Edit, Write, Glob, Grep) rather than shell commands for file operations.
- Prefer editing existing files over creating new ones.
- Do not create documentation or README files unless explicitly asked.

### Risky Actions — Always Confirm First

Pause and ask the user before performing:

- Destructive git operations (`reset --hard`, `push --force`, branch deletion)
- Dropping or migrating databases
- Deleting files or directories
- Modifying CI/CD pipelines
- Pushing to `master`/`main` directly
- Sending messages to external services

A user approving an action once does **not** grant blanket approval for all future similar actions.

### Task Management

For multi-step tasks (3+ steps), use a todo list to track progress. Mark each task complete immediately when done — do not batch completions.

---

## Setup & Onboarding (Placeholder)

Once the project stack is defined, add setup instructions here:

```bash
# Clone the repo
git clone http://local_proxy@127.0.0.1:57049/git/Ubermensch-6920/CC
cd CC

# Install dependencies (update when stack is chosen)
# e.g.: npm install | pip install -r requirements.txt

# Run tests (update when test framework is chosen)
# e.g.: npm test | pytest

# Start development server (update when applicable)
# e.g.: npm run dev
```

---

## Updating This File

Update CLAUDE.md whenever:

- A new tech stack or language is introduced
- Linting, formatting, or build tooling is configured
- Test conventions are established
- Significant architectural decisions are made
- New development workflow steps are added

Keep this file accurate and concise — it is the primary source of truth for AI assistants working in this repo.
