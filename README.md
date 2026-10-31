# Inverting Entropy

A professional portfolio exploring data science, artificial intelligence, software engineering, and some personal hobbies.

## Overview

**Inverting Entropy** is a personal portfolio and software engineering project designed to showcase technical work, best practices, and demonstrate a thoughtful approach to building software with modern development tools and AI coding agents.

The project is being developed incrementally, with an emphasis on maintainable code, clear documentation, version control, and verifiable results.

## Project Goals

- Build a polished, responsive professional portfolio.
- Showcase technical projects, skills, and ongoing professional development.
- Strengthen foundation in HTML, CSS, JavaScript, Git, and GitHub.
- Use AI coding agents within a structured, reviewable development workflow.
- Document architectural decisions, requirements, implementation choices, and lessons learned.
- Automate appropriate checks to improve reliability and maintainability.
- Publish the finished website using a custom domain.

## Planned Technology Stack

| Technology | Intended purpose |
|---|---|
| HTML | Semantic page structure and accessible content |
| CSS | Responsive layouts, visual design, and styling |
| JavaScript | Interactive behavior where it adds value |
| Git | Local version control and change history |
| GitHub | Source hosting, issues, pull requests, and project documentation |
| GitHub Pages | Static website hosting |
| AI coding agent | Bounded implementation tasks, explanations, and development assistance |

The initial implementation will favor native web technologies over a framework. Additional dependencies will be introduced only when a clear requirement justifies their complexity.

## Development Principles

**Small, reviewable changes.** Work should be organized into focused tasks with explicit acceptance criteria and meaningful commits.

**Verify before merging.** Changes should be inspected and checked before they are considered complete.

**Document decisions.** Important design and architectural choices should include their rationale and trade-offs.

**Keep a human in the loop.** AI agents may propose and implement changes, but significant decisions, verification, and final approval remain under human control.

**Protect sensitive information.** The public repository must not contain credentials, private personal information, classified information, or proprietary material from employers or customers.

**Use industry best practices.** Design and development should follow industry best practices.

## Project Status

**Current phase:** HTML foundation implemented; portfolio implementation in progress.

Documentation established:
- `AGENTS.md` defines agent instructions and approval boundaries.
- `docs/requirements.md` records MVP requirements and open decisions; its status remains draft pending review.
- `docs/design.md` specifies Graphite & Ember, with an approved palette and final visual review pending.
- `docs/architecture.md` describes the proposed static architecture and root-level website layout.

Implemented, awaiting human review:
- Root-level `index.html` with semantic landmarks, section headings, a visible skip link, and internal navigation.
- Hero, background, skills, projects, contact, and footer regions using clearly labeled development placeholders where content approval is pending.
- Core content and links are written directly in HTML without JavaScript or external resources.

Not yet implemented or deployed:
- Graphite & Ember styling, responsive layout treatment, and computational artwork.
- Approved professional copy, skills, project entries, profile URLs, and a working contact mechanism.
- Full browser, accessibility, and performance verification and appropriate automated checks.
- GitHub Pages publishing, custom-domain configuration, and production HTTPS verification.
- Dedicated agent workflow documentation and architectural decision records when needed.

The HTML foundation does not establish MVP completion or release readiness. Deployment has not been performed as part of this work.

## Repository Structure

Current files:

```text
.
├── index.html
├── README.md
├── AGENTS.md
├── .gitignore
├── LICENSE
└── docs/
    ├── requirements.md
    ├── design.md
    └── architecture.md
```

The root-level entry point follows `docs/architecture.md`. Planned additions, created only when needed and approved, include:

```text
.
├── .nojekyll
├── assets/
│   ├── css/styles.css
│   ├── js/main.js          # Optional; only for justified behavior
│   ├── images/hero-visual.svg
│   └── icons/
├── docs/
│   ├── agent-workflow.md
│   └── decisions/
└── tests/
```

These additions do not currently exist. No dependencies, build tools, or CI workflows are required for the HTML foundation.

## Development Workflow

The project will use a branch-based workflow:

1. Define a task and its acceptance criteria.
2. Create a focused working branch.
3. Implement the change, using an AI coding agent when appropriate.
4. Inspect the diff and understand the implementation.
5. Run relevant checks and review the results.
6. Commit the change with a descriptive message.
7. Merge reviewed work into `main`.

Documentation will capture important requirements, decisions, and verification steps so the repository communicates not only what was built, but also how and why it was built.

### Local preview

No installation or build step is required. Open `index.html` directly in a browser, or run Python's standard-library server from the repository root:

```bash
python3 -m http.server 8000 --bind 127.0.0.1
```

Visit `http://127.0.0.1:8000` and stop the server with `Ctrl+C`. This is a local preview, not a production deployment.

For manual review, follow the skip link and section links with Tab, Shift+Tab, and Enter; check native focus visibility and rendering at 320, 375, 768, and 1440 CSS pixels. The page contains no JavaScript. These instructions do not imply that browser or accessibility checks have passed. Deployment instructions will be added when publishing is approved and verified.

## License

See [LICENSE](LICENSE) for the terms governing this project. The license applies subject to its stated terms; third-party assets and dependencies may have separate licensing requirements.
