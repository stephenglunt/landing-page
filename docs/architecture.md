# Inverting Entropy — System Architecture

**Version:** 0.1.0
**Status:** Architecture documented — HTML foundation and initial content implemented; visual implementation pending
**Project:** Inverting Entropy
**Related documents:** `README.md`, `AGENTS.md`, `docs/requirements.md`, `docs/design.md`

## 1. Architectural Overview

Inverting Entropy will initially be implemented as a static, single-page professional portfolio.

The architecture prioritizes:

- Understandability.
- Minimal dependencies.
- Accessibility.
- Performance.
- Maintainability.
- Straightforward local development and deployment.
- Compatibility with AI-assisted development workflows.

The website will use semantic HTML, modern CSS, and vanilla JavaScript only where interactivity is justified.

There will be no backend application, database, client-side routing framework, or JavaScript build system for the MVP.

## 2. Architecture Decision

### Selected Approach: Static Website with Native Web Technologies

The browser will request HTML, CSS, JavaScript, and static assets from GitHub Pages.

HTML will provide the document structure and content.

CSS will control the Graphite & Ember visual design, responsive layout, and visual interaction states.

JavaScript will be used only for behavior that cannot be adequately implemented using native HTML and CSS.

### Alternatives Considered

**React or another frontend framework**

Advantages:
- Component abstractions.
- Extensive ecosystem.
- Useful for increasingly complex interactive interfaces.

Disadvantages:
- Additional dependencies and tooling.
- More abstractions to learn.
- Unnecessary complexity for the initial portfolio.

**Static site generator**

Advantages:
- Reusable templates.
- Structured content.
- Useful for larger collections of articles and project pages.

Disadvantages:
- Additional build and deployment requirements.
- More configuration than the MVP currently needs.

**Native HTML, CSS, and JavaScript**

Advantages:
- Small deployment footprint.
- Direct understanding of browser technologies.
- Minimal dependencies.
- Easy to inspect and debug.
- Simple static hosting.

Disadvantages:
- Less built-in component reuse.
- Manual content management.
- May require refactoring as the number of pages grows.

### Decision

Use native HTML, CSS, and JavaScript for the MVP.

Reevaluate this decision if content volume, reuse requirements, or interactive complexity materially increases.

## 3. Repository Structure

The proposed structure is:

```text
.
├── index.html
├── .nojekyll
├── assets/
│   ├── css/
│   │   └── styles.css
│   ├── js/
│   │   └── main.js
│   ├── images/
│   │   └── hero-visual.svg
│   └── icons/
├── docs/
│   ├── requirements.md
│   ├── design.md
│   ├── architecture.md
│   └── decisions/
├── tests/
├── README.md
├── AGENTS.md
├── .gitignore
└── LICENSE
```

Only create files and directories when they are needed. The architecture describes the intended layout rather than the current filesystem.

### Directory Responsibilities

**Repository root**
- `index.html`: Website entry point and semantic content.
- `.nojekyll`: Disables Jekyll processing for direct static publishing when GitHub Pages is configured from a branch.

**`assets/css/`**
- Visual tokens.
- Responsive layouts.
- Component styling.
- Interaction states.
- Reduced-motion behavior.

**`assets/js/`**
- Minimal optional browser interactivity.
- No essential content generation or client-side routing.

**`assets/images/`**
- Optimized static imagery.
- Computational SVG artwork.
- Relevant approved project visuals.

**`assets/icons/`**
- Local icon assets, if needed.

**`docs/`**
- Requirements and architecture.
- Visual design specification.
- Architectural decisions.
- Future agent workflow documentation.

**`tests/`**
- Automated checks when introduced.
- No test framework is required merely to create the initial static page.

## 4. HTML Architecture

The initial website will use one semantic HTML document.

Proposed major regions:

```html
<body>
  <a href="#main">Skip to content</a>

  <header>
    <!-- Site identity and navigation -->
  </header>

  <main id="main">
    <section id="home"></section>
    <section id="about"></section>
    <section id="skills"></section>
    <section id="projects"></section>
    <section id="contact"></section>
  </main>

  <footer></footer>
</body>
```

This represents the intended semantic hierarchy, not a complete implementation.

### Requirements

- Use a single primary page heading.
- Use descriptive section headings.
- Use native links for navigation.
- Maintain a logical reading order.
- Provide a visible skip link on keyboard focus.
- Preserve meaningful content when JavaScript is unavailable.
- Do not generate essential content exclusively through JavaScript.

Navigation will use ordinary fragment links.

No client-side router is required.

## 5. CSS Architecture

The MVP will use a single stylesheet:

`assets/css/styles.css`

Organize the stylesheet using clearly labeled sections:

1. Design tokens.
2. Reset and base styles.
3. Typography.
4. Layout utilities.
5. Header and navigation.
6. Hero.
7. About.
8. Skills.
9. Projects.
10. Contact and footer.
11. Responsive adjustments.
12. Accessibility and reduced-motion rules.

This is an organizational guideline, not a requirement to create separate files for every section.

### Design Tokens

Use CSS custom properties for approved colors and spacing.

The Graphite & Ember palette defined in `docs/design.md` is authoritative.

Tokens include:

```css
:root {
  --color-background: #101318;
  --color-surface: #1B2028;
  --color-surface-elevated: #272E38;

  --color-text: #F4F6F8;
  --color-text-muted: #AEB8C4;

  --color-accent: #FFB000;
  --color-accent-secondary: #FF683B;

  --color-border: #39434F;
  --color-on-accent: #101318;
  --color-focus: #FFB000;
}
```

Prefer reusable tokens and component classes over duplicated literal values.

Avoid unnecessary specificity, inline styles, and premature utility-class abstractions.

## 6. JavaScript Architecture

JavaScript will provide progressive enhancement only.

Examples of potentially justified behavior:

- Optional navigation enhancements.
- Small user-interface interactions.
- Future interactive computational visualizations.

### Constraints

- No frontend framework for MVP.
- No runtime dependencies without approval.
- No JavaScript required to render core professional content.
- No unnecessary network requests.
- Use modern browser APIs and understandable functions.
- Avoid global state unless necessary.

If the MVP requires no JavaScript behavior, `assets/js/main.js` may be omitted.

## 7. Computational Visual Architecture

### Selected Initial Approach: Static SVG

The hero section will include a decorative computational illustration expressing the concept of structure emerging from complexity.

The artwork will be stored as a local SVG asset.

The composition may contain:

- Dispersed nodes.
- Ordered node patterns.
- Fine connecting lines.
- Geometric or mathematical structures.
- Amber and orange focal points against neutral graphite.

### Design Requirements

- Visually reinforce the Inverting Entropy identity.
- Remain subordinate to primary content.
- Scale appropriately across viewport sizes.
- Require no external library.
- Display without JavaScript.
- Avoid essential information in the illustration.

When the SVG is purely decorative, its HTML presentation must exclude it from the accessibility tree without hiding interactive content.

### Future Animation

Animation is deferred beyond the initial implementation.

If approved later:

- Prefer simple CSS animation where sufficient.
- Respect `prefers-reduced-motion`.
- Avoid continuous high-cost rendering.
- Preserve the static visual as a fallback.
- Introduce JavaScript animation only when justified by a specific requirement.

## 8. Content Architecture

The initial page content will be maintained directly in semantic HTML.

Content categories:

- Hero and introduction.
- Professional background.
- Technical skills.
- Selected projects.
- Professional links and contact information.

### Project Entries

Each published project entry should include:

- Title.
- Problem or objective.
- Technical approach.
- Relevant technologies.
- Outcome or current status.
- Relevant public link, where available.

Only approved, publicly shareable information may be included.

If the number of projects or pages becomes difficult to maintain manually, reconsider content templates or a static site generator.

## 9. Local Development

No package manager, build command, or dependency installation is required for the MVP.

### Preferred Local Preview

Use Python's standard-library HTTP server:

```bash
python3 -m http.server 8000
```

Run the command from the repository root to preview the existing `index.html`.

Open:

`http://localhost:8000`

The server is for local development only and is not a production hosting solution.

Use `Ctrl+C` to stop it.

### Development Environment

- macOS.
- Visual Studio Code.
- Git.
- A modern browser.
- Python 3, for the optional local static server.

Browser developer tools will be used to inspect layout, accessibility, network requests, and console errors.

## 10. Deployment Architecture

### Hosting

The MVP will use GitHub Pages.

### Initial Publishing Strategy

Publish static files from:

- Branch: `main`.
- Folder: `/` (repository root).

Because this project does not require a build process, branch-based deployment is the simplest initial strategy.

Create `.nojekyll` in the publishing root to prevent unnecessary Jekyll processing.

Deployment configuration will not be enabled until the first release is approved.

### Custom Domain

The production domain will be configured after the initial site is verified.

The domain name and DNS changes require explicit human approval.

HTTPS must be enabled and verified for the production release.

### Asset Paths

Prefer relative paths such as:

```html
<link rel="stylesheet" href="./assets/css/styles.css">
```

Avoid hard-coded site-root absolute asset paths for the initial implementation, allowing the page to work under a GitHub Pages project URL and later under a custom domain.

### Publication Considerations

GitHub Pages publishes website files, but does not provide backend application hosting.

Production deployment will require verification of:

- Page availability.
- Asset loading.
- Navigation.
- HTTPS.
- Responsive behavior.
- Custom-domain configuration.

## 11. Verification Strategy

### Initial Manual Verification

For each implementation task:

- Inspect Git changes.
- Confirm HTML and CSS render in the browser.
- Check developer console errors.
- Test navigation with mouse and keyboard.
- Test narrow and wide viewport sizes.
- Confirm essential content works without JavaScript.
- Check links and asset paths.

### Accessibility Verification

- Use semantic HTML.
- Test keyboard navigation and focus visibility.
- Verify relevant contrast ratios.
- Check image descriptions and decorative handling.
- Review heading structure.
- Perform automated checks when tooling becomes available.
- Conduct manual review because automated checks cannot establish full accessibility compliance.

### Performance Verification

- Inspect unnecessary asset downloads.
- Optimize images and SVGs.
- Avoid unnecessary JavaScript.
- Evaluate the deployed site using Lighthouse against the requirements.

### Future Automation

Automated checks may later include:

- HTML validation.
- Link checking.
- Accessibility auditing.
- JavaScript linting if needed.
- Deployment verification.

No test dependencies or CI workflows are authorized by this architecture alone.

## 12. Security and Privacy

- Do not commit credentials or API keys.
- Do not publish classified, proprietary, or private information.
- Do not add third-party analytics or tracking to the MVP.
- Avoid unnecessary remote asset dependencies.
- Review all publicly visible content before deployment.
- Treat GitHub Pages as a public publishing surface.

Client-side code and assets must not contain secrets.

## 13. Agent-Assisted Development

AI coding agents must follow `AGENTS.md`.

Implementation tasks should include:

- Relevant requirement IDs.
- Approved scope.
- Expected files.
- Acceptance criteria.
- Verification instructions.
- Explicit approval boundaries.

Agents should not independently introduce frameworks, services, dependencies, or deployment infrastructure.

### Recommended Agent Task Sequence

1. Create the basic semantic HTML page.
2. Implement the Graphite & Ember design tokens and layout.
3. Implement responsive navigation and section styling.
4. Create the computational SVG.
5. Add approved professional content and projects.
6. Perform accessibility and performance checks.
7. Prepare a reviewed deployment.

Each task should be small enough to independently understand, verify, and review.

## 14. Architectural Trade-offs

| Decision | Benefit | Trade-off |
|---|---|---|
| Static website | Simplicity and speed | Limited dynamic features |
| Native HTML/CSS/JS | Direct learning and low overhead | More manual content management |
| Single HTML page | Straightforward navigation and deployment | May become unwieldy as content grows |
| One stylesheet | Easy initial maintenance | May need splitting later |
| Static SVG | Lightweight computational identity | No dynamic interaction initially |
| GitHub Pages | Simple hosting integration | Static hosting and publishing constraints |
| No build system | Fewer moving parts | Less automated asset processing |

## 15. Architecture Review Triggers

Reevaluate the architecture if:

- Multiple independent content pages are required.
- Significant content duplication emerges.
- The project needs dynamic data or server-side functionality.
- Interactive visualizations become substantially complex.
- Manual content updates become error-prone.
- A dependency or build process has a demonstrated benefit.

Any material architecture change requires human approval and an appropriate decision record.

## 16. MVP Architecture Acceptance Criteria

The architecture is ready for implementation when:

- The intended file structure is documented.
- The static hosting strategy is established.
- The HTML/CSS/JavaScript responsibilities are defined.
- The computational visual approach is specified.
- Local preview and verification procedures are documented.
- Security and approval boundaries are established.
- Any deviations from the approved requirements are resolved.

**Current status:** Semantic HTML foundation approved; initial professional content implemented for review. Styling, computational artwork, full browser/accessibility/performance verification, and deployment remain pending. Architectural decisions are unchanged.
