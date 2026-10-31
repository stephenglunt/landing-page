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

**Current phase:** Repository foundation.

Completed:
- Created the GitHub repository.
- Initialized the repository with a README, `.gitignore`, and license.
- Cloned the repository into the local development folder.
- Verified the local Git configuration and repository connection.
- Created the `chore/project-foundation` working branch.

Planned:
- Establish agent instructions and project documentation.
- Define website requirements and design direction.
- Implement the initial responsive landing page.
- Add appropriate validation and automated checks.
- Publish the website and configure the custom domain.
- Develop a documented workflow for AI-assisted implementation and review.

This status will be updated as work is completed. Planned features are not represented as implemented or deployed.

## Repository Structure

The repository will evolve as the project develops. The anticipated structure includes:

```text
.
├── README.md
├── AGENTS.md
├── .gitignore
├── docs/
│   ├── requirements.md
│   ├── architecture.md
│   ├── agent-workflow.md
│   └── decisions/
├── src/
├── tests/
└── .github/
    └── workflows/
```

Directories and files will be added when they serve an actual project need; this is a target structure, not a claim that all components already exist.

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

### Current development state

The repository is currently in its foundation phase. The website implementation and deployment instructions will be added as those capabilities are developed and verified.

## License

See [LICENSE](LICENSE) for the terms governing this project. The license applies subject to its stated terms; third-party assets and dependencies may have separate licensing requirements.
