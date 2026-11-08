# Ralph Agent Instructions

## Overview

Ralph is an autonomous AI agent loop that runs AI coding tools repeatedly until all PRD items are complete. Each iteration is a fresh instance with clean context.

For this project, run the Ralph loop using **Claude Code with Claude Haiku 5.5**.

## Project Rules

These rules apply to every agent and every Ralph iteration.

### Secrets and Personal Information

- Never commit secrets: API keys, tokens, passwords, credentials, private keys, or `.env` files.
- Never commit personally identifiable information (PII), such as phone numbers, email addresses, home addresses, or other private personal details, unless the user has explicitly approved it for publication.
- Check staged changes (`git diff --cached`) for secrets and PII before every commit.
- If you find a secret or PII already in the repository, stop and report it instead of committing over it.

### Technology Stack

- Build the site with HTML, CSS, and vanilla JavaScript only.
- Do not add dependencies of any kind: no npm packages, frameworks, libraries, CDN scripts or stylesheets, web fonts, or build tools.
- Do not create `package.json` or other package-manager files.
- If a story seems to require a dependency, stop and report it instead of adding one.

## Required Model Configuration

- Always run Ralph with `--tool claude`.
- Every Claude Code invocation in `ralph.sh` must explicitly include:
  ```bash
  --model claude-haiku-5-5
  ```
- Preserve the script's other arguments, prompt input, and output handling when adding the model flag.
- Do not rely on the default Claude Code model or the `haiku` alias.
- Do not switch to Amp or another model unless the user explicitly requests it.
- If Claude Haiku 5.5 is unavailable, stop and report the error instead of falling back to another model.
- When modifying `ralph.sh`, preserve this model requirement.

## Commands

```bash
# Run Ralph from scripts/ralph/
cd scripts/ralph
# Requires ralph.sh to pass --model claude-haiku-5-5 to Claude Code
./ralph.sh --tool claude [max_iterations]
```

## Key Files

All Ralph files live in `scripts/ralph/`; `ralph.sh` reads them from its own directory.

- `scripts/ralph/ralph.sh` - Bash loop that spawns fresh AI instances. Supports Amp and Claude Code; this project requires Claude Code with `--model claude-haiku-5-5`.
- `scripts/ralph/CLAUDE.md` - Instructions given to each Claude Code instance.
- `scripts/ralph/prompt.md` - Instructions given to each Amp instance; unused in this project's required configuration.
- `scripts/ralph/prd.json.example` - Example PRD format. The active PRD must be saved as `scripts/ralph/prd.json`.
- `scripts/ralph/progress.txt` - Progress log appended by each iteration (created by `ralph.sh` on first run).

## Patterns

- Each iteration spawns a fresh Claude Code instance using Claude Haiku 5.5 with clean context.
- Memory persists via git history, `progress.txt`, and `prd.json`.
- Stories should be small enough to complete in one context window.
- Record discovered patterns for future iterations by adding them to this Patterns section only. Never modify the Project Rules section.
