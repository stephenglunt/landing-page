# Inverting Entropy — Website Requirements

**Version:** 0.1.0
**Status:** Draft — pending review
**Project:** Inverting Entropy
**Release target:** MVP (v1.0)

## 1. Purpose

Inverting Entropy is a professional portfolio website intended to demonstrate technical expertise, showcase selected projects, and communicate an engineering approach grounded in analytical thinking, maintainable software, and responsible use of AI-assisted development.

The initial release will be a publicly accessible, responsive static website.

## 2. Target Audience

### Primary audience
- Technical recruiters and hiring managers.
- Software engineering, data science, and AI/ML engineering leaders.
- Technical professionals evaluating project work and engineering capabilities.

### Secondary audience
- Potential collaborators.
- Other developers interested in documented engineering workflows.
- Visitors interested in technical writing and project explanations.

## 3. Product Objectives

| ID | Objective |
|---|---|
| OBJ-01 | Establish a credible and distinctive professional identity. |
| OBJ-02 | Make technical skills and areas of expertise easy to identify. |
| OBJ-03 | Provide evidence of technical capabilities through selected projects. |
| OBJ-04 | Make it easy for visitors to explore source code and initiate professional contact. |
| OBJ-05 | Demonstrate thoughtful software engineering practices through the public repository. |
| OBJ-06 | Provide a foundation for future technical articles and project case studies. |

## 4. Scope

### 4.1 MVP — Included

The initial release will include:

- A responsive, single-page professional portfolio.
- A distinctive visual identity using the name Inverting Entropy.
- An introduction or hero section.
- A concise professional background section.
- A technical skills section.
- A selected projects section.
- Links to relevant professional profiles.
- A contact mechanism.
- Basic accessibility, performance, and SEO support.
- Deployment to a custom domain.

### 4.2 Future Enhancements — Excluded from MVP

The following are potential future capabilities, not committed MVP requirements:

- A technical blog or article publishing system.
- Individual project case-study pages.
- A content management system.
- User accounts or authentication.
- A backend API.
- Database integration.
- A contact form requiring server-side processing.
- Analytics or visitor tracking.
- Complex animations or interactive visualizations.
- AI-powered visitor-facing features.

These features require separate justification and approval before implementation.

## 5. Functional Requirements

### FR-01 — Site Identity and Navigation

**Priority:** Must have

The website shall:

- Display the name Inverting Entropy prominently.
- Provide navigation to the main page sections.
- Allow users to navigate using a keyboard.
- Provide a clear visual indication of the current keyboard focus.
- Maintain usable navigation on narrow screens.

**Acceptance criteria:**
- All primary navigation links lead to valid page sections.
- Navigation is usable at desktop and mobile viewport widths.
- Keyboard-only navigation can reach all interactive navigation elements.

### FR-02 — Hero Section

**Priority:** Must have

The hero section shall:

- Present a concise professional headline.
- Explain the website's purpose in one or two short paragraphs.
- Provide at least one prominent action leading to projects or professional contact.

**Acceptance criteria:**
- A visitor can identify the professional focus of the site without scrolling.
- The primary action has a clear label and functional destination.
- Content remains readable on small screens.

### FR-03 — Professional Background

**Priority:** Must have

The website shall provide a concise overview of relevant professional experience, areas of specialization, and technical interests.

**Acceptance criteria:**
- The section is understandable to a technically informed recruiter.
- Claims are factual, supportable, and approved for public disclosure.
- Sensitive or proprietary information is excluded.

### FR-04 — Technical Skills

**Priority:** Must have

The website shall display technical capabilities organized into meaningful categories.

Candidate categories include:

- Programming languages.
- AI and machine learning.
- Data engineering and analytics.
- Cloud infrastructure and development tools.
- Software engineering practices.

**Acceptance criteria:**
- Skills are organized and easy to scan.
- Displayed skills reflect actual experience.
- The layout remains usable on mobile devices.

### FR-05 — Selected Projects

**Priority:** Must have

The website shall showcase selected technical projects.

Each published project entry shall include:

- Project title.
- Brief problem or objective statement.
- Summary of the technical approach.
- Relevant technologies.
- A functional link to a repository, demonstration, or detailed explanation, where publicly available.

**Acceptance criteria:**
- Project descriptions distinguish completed work from ongoing work.
- All published links are functional.
- Project descriptions do not disclose restricted or proprietary information.
- At least one approved project entry is available for the MVP.

### FR-06 — Professional Links and Contact

**Priority:** Must have

The website shall provide a way for visitors to explore professional profiles and initiate contact.

**Acceptance criteria:**
- The site includes a working GitHub profile link.
- Other professional links are included only when provided and approved.
- A working contact mechanism is available.
- No private contact details are published without approval.

### FR-07 — Footer

**Priority:** Should have

The website should provide a footer containing appropriate site identity, navigation, or professional links.

**Acceptance criteria:**
- The footer does not obscure or overlap other content.
- Footer links function correctly.
- Footer content remains legible at mobile widths.

## 6. Nonfunctional Requirements

### NFR-01 — Responsive Design

**Priority:** Must have

The website shall support desktop, tablet, and mobile screen sizes without horizontal scrolling caused by the layout.

**Acceptance criteria:**
- The page is usable at viewport widths of 320, 375, 768, and 1440 CSS pixels.
- Text does not overlap or become clipped.
- Navigation and interactive elements remain accessible.

### NFR-02 — Accessibility

**Priority:** Must have

The website shall target WCAG 2.2 Level AA for applicable requirements.

**Acceptance criteria:**
- Semantic HTML is used appropriately.
- All functionality is keyboard accessible.
- Visible keyboard focus is provided.
- Normal text contrast is at least 4.5:1, subject to WCAG exceptions.
- Images have appropriate alternative text or are marked decorative.
- Heading structure is logical.
- Reduced-motion preferences are respected where motion is used.
- Automated accessibility checks are performed, with manual checks for criteria that automation cannot establish.

### NFR-03 — Performance

**Priority:** Must have

The website shall prioritize fast loading and minimal unnecessary JavaScript.

**Initial performance targets:**
- Lighthouse Performance score of at least 90 on the deployed homepage under a documented test configuration.
- Lighthouse Accessibility score of at least 90.
- No unnecessary third-party scripts.
- Images appropriately sized and optimized.

Lighthouse scores are diagnostic targets, not substitutes for real-user performance or accessibility testing.

### NFR-04 — Browser Compatibility

**Priority:** Must have

The website shall function in current stable versions of Chrome, Firefox, Safari, and Edge.

**Acceptance criteria:**
- Core content and navigation remain usable in each browser.
- No browser-specific feature prevents access to essential content.

### NFR-05 — Search Engine Discoverability

**Priority:** Should have

The website should include:

- A meaningful page title.
- A concise meta description.
- Appropriate heading hierarchy.
- Descriptive link text.
- A canonical URL once the production domain is established.

**Acceptance criteria:**
- Required metadata is present in the published HTML.
- No unintended indexing restrictions are introduced.

### NFR-06 — Security and Privacy

**Priority:** Must have

The website shall:

- Avoid exposing secrets or sensitive information.
- Use HTTPS for the published site.
- Avoid unnecessary collection of visitor information.
- Avoid third-party tracking in the MVP.
- Avoid dependencies that are not justified by requirements.

### NFR-07 — Maintainability

**Priority:** Must have

The implementation shall:

- Favor semantic HTML, CSS, and vanilla JavaScript initially.
- Use understandable naming and organization.
- Avoid unnecessary frameworks and build systems.
- Keep documentation aligned with implementation.
- Support reproducible local development and verification.

## 7. Technical Constraints

The initial implementation is constrained as follows:

| Area | Constraint |
|---|---|
| Frontend | HTML, CSS, and vanilla JavaScript |
| Hosting | GitHub Pages |
| Source control | Git and GitHub |
| Development environment | VS Code |
| Dependencies | Minimize; require approval before adding |
| Deployment | Static website with custom domain |
| Backend | None for MVP |
| Database | None for MVP |
| Agent instructions | Follow repository `AGENTS.md` |

These constraints may change through an explicitly documented architectural decision.

## 8. Content Requirements

All published content must be reviewed for accuracy, relevance, and suitability for public release.

Content should emphasize demonstrated capabilities and outcomes rather than unsupported claims.

Initial content categories:

- Professional introduction.
- Technical skills.
- Selected projects.
- Professional links.
- Contact information or contact mechanism.

Placeholder content may be used during development but must be clearly identified and replaced or removed before public release.

## 9. Definition of MVP Completion

The MVP is ready for release when:

- All Must Have functional requirements are satisfied.
- All Must Have nonfunctional requirements have been evaluated, with any exceptions explicitly reviewed and approved.
- Published content has been approved.
- Required links function correctly.
- Responsive behavior has been tested at the specified widths.
- Accessibility checks have been performed and findings addressed or documented.
- Performance targets have been evaluated.
- The website is available over HTTPS at the approved custom domain.
- Deployment and local development instructions are documented.
- The release has received human approval.

## 10. Open Decisions

The following decisions remain unresolved and must be settled before their dependent implementation tasks:

| ID | Decision | Status |
|---|---|---|
| DEC-01 | Visual identity, color palette, and typography | Open |
| DEC-02 | Final professional headline and introductory copy | Open |
| DEC-03 | Initial portfolio projects and approved descriptions | Open |
| DEC-04 | Professional profile URLs | Open |
| DEC-05 | Contact mechanism | Open |
| DEC-06 | Production domain and DNS configuration | Open |
| DEC-07 | Whether the initial design includes a portrait or other imagery | Open |

## 11. Change Management

Requirements changes should be made through focused commits or pull requests.

Material changes should include:

- The reason for the change.
- Requirements affected.
- Consequences for design, implementation, or verification.
- Updated acceptance criteria where applicable.

Coding agents must not silently expand project scope or treat proposed future enhancements as approved requirements.
