# Inverting Entropy — Visual Design Specification

**Version:** 0.1.0
**Status:** Proposed — pending implementation and visual review
**Related document:** `docs/requirements.md`

## 1. Design Concept

**Theme:** Structure emerging from complexity.

Inverting Entropy combines technical minimalism with restrained computational visuals to communicate precision, analytical thinking, and the transformation of complex information into useful systems.

The site should feel credible, sophisticated, and technically distinctive.

### Design Principles

1. **Content first:** Professional experience, technical capabilities, and projects take precedence over decoration.
2. **Structured complexity:** Computational patterns communicate the site's identity without reducing legibility.
3. **Visual restraint:** Limit colors, typography variations, animation, and ornamental elements.
4. **Progressive enhancement:** Core content and navigation must work without JavaScript.
5. **Consistency:** Reuse established spacing, colors, typography, and component patterns.

## 2. Color System — Graphite & Ember

**Status:** Approved palette; implementation pending.

The visual identity uses neutral graphite backgrounds with saturated amber and orange accents.

Warmth should come primarily from the accents rather than from brown-tinted surfaces. The result should be vibrant, precise, modern, and visually restrained.

### 2.1 Color Tokens

| Token | Value | Usage |
|---|---|---|
| `--color-background` | `#101318` | Main page background |
| `--color-surface` | `#1B2028` | Cards and secondary sections |
| `--color-surface-elevated` | `#272E38` | Elevated elements |
| `--color-text` | `#F4F6F8` | Primary text |
| `--color-text-muted` | `#AEB8C4` | Supporting text |
| `--color-accent` | `#FFB000` | Primary actions, links, highlights |
| `--color-accent-secondary` | `#FF683B` | Secondary highlights and computational graphics |
| `--color-border` | `#39434F` | Decorative borders and separators |

### 2.2 CSS Token Definitions

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

The final two variables are semantic aliases of approved palette colors, not additional palette colors.

### 2.3 Color Usage Rules

- Use graphite and neutral gray for backgrounds and structural elements.
- Use warm off-white for primary text and muted gray for supporting text.
- Use amber for primary calls to action, active highlights, and important technical labels.
- Use orange for secondary emphasis and selected computational visual elements.
- Do not use amber or orange for large blocks of body text or large background regions.
- Avoid brown, beige, pastel colors, and unnecessary additional accent colors.
- Use color consistently and never as the sole means of conveying information.

### 2.4 Contrast Requirements

The design targets WCAG 2.2 Level AA.

Required contrast thresholds:

- Normal text: at least 4.5:1.
- Large text: at least 3:1.
- Required visual information identifying controls and meaningful graphics: at least 3:1 against adjacent colors.

Verified initial color pairs:

| Foreground | Background | Ratio | Result |
|---|---|---:|---|
| `#F4F6F8` | `#101318` | 17.18:1 | Pass |
| `#AEB8C4` | `#101318` | 9.26:1 | Pass |
| `#AEB8C4` | `#1B2028` | 8.14:1 | Pass |
| `#FFB000` | `#101318` | 10.16:1 | Pass |
| `#FF683B` | `#101318` | 6.47:1 | Pass |
| `#101318` | `#FFB000` | 10.16:1 | Pass |
| `#101318` | `#FF683B` | 6.47:1 | Pass |
| `#F4F6F8` | `#FFB000` | 1.69:1 | Fail for normal text |
| `#F4F6F8` | `#FF683B` | 2.66:1 | Fail for normal text |

These ratios apply to the specified opaque colors. Blending, transparency, gradients, overlays, and other background combinations must be tested separately.

### 2.5 Buttons and Links

**Primary buttons**

- Background: `#FFB000`.
- Text: `#101318`.
- Use a clearly visible hover treatment.
- Provide a keyboard focus outline independent of hover.

**Secondary buttons**

- Prefer a graphite background with light text.
- Use amber or orange for a sufficiently visible outline, underline, or accent.
- Do not rely on the standard border color alone to identify an interactive control.

**Links**

- Amber is the preferred link color on dark backgrounds.
- Links within body text should also have an underline or another non-color-only distinction where needed.
- Hover and focus states must remain clearly distinguishable.

### 2.6 Focus Indicators

Use a visible, high-contrast keyboard focus treatment.

Recommended initial implementation:

```css
:focus-visible {
  outline: 3px solid var(--color-focus);
  outline-offset: 3px;
}
```

Focus indicators must not be clipped or obscured.

The proposed outline must be checked against its actual adjacent colors, including filled amber controls. Where an amber outline would blend into an amber control, use spacing, a contrasting intermediate ring, or another verified focus treatment.

### 2.7 Borders and Surfaces

The standard border color `#39434F` is intended primarily for subtle decorative structure.

It does not independently satisfy the 3:1 non-text contrast threshold against the background or surface colors.

Therefore:

- Decorative dividers may use the standard border.
- Essential control boundaries must use a stronger visible treatment.
- Inputs and interactive elements must remain identifiable without relying on low-contrast borders.
- Hover, selected, disabled, and focus states must be evaluated individually.

### 2.8 Computational Visualization Colors

The hero visualization should use:

- Graphite and slate tones for structural lines and inactive nodes.
- Amber for organized structures, selected nodes, and focal points.
- Orange for limited secondary emphasis or transitions.

The intended visual metaphor is a transition from dispersed complexity to ordered structure.

Use restrained color distribution so the visualization supports rather than competes with the headline.

Decorative elements may use reduced opacity, provided they do not communicate essential information. Meaningful graphical elements must meet applicable contrast requirements.

### 2.9 Design Validation

Before MVP release:

- Verify all actual foreground/background combinations.
- Test primary and secondary buttons in default, hover, focus, and active states.
- Check navigation, links, and interactive controls using keyboard navigation.
- Verify meaningful graphical elements meet applicable non-text contrast requirements.
- Test visual behavior at all required viewport widths.
- Perform automated accessibility checks and manual review.

The palette's contrast calculations are complete, but full interface accessibility remains unverified until implementation.

## 3. Typography

### Font Families

Primary:

```css
font-family: system-ui, -apple-system, BlinkMacSystemFont,
             "Segoe UI", sans-serif;
```

Technical labels:

```css
font-family: ui-monospace, SFMono-Regular, Menlo,
             Consolas, monospace;
```

### Type Scale

| Role | Proposed size |
|---|---|
| Hero heading | `clamp(2.75rem, 6vw, 5rem)` |
| Section heading | `clamp(1.75rem, 3vw, 2.5rem)` |
| Card heading | `1.25rem` |
| Body text | `1rem` |
| Supporting text | `0.875rem` |
| Technical label | `0.75rem` |

Use a base line-height of approximately 1.6 for body text and tighter line-height for large headings.

Avoid using monospace for long paragraphs.

## 4. Layout System

### Content Width

- Maximum content width: 1200px.
- Main reading text: approximately 65–75 characters per line.
- Responsive horizontal padding: 20px on small screens, increasing on larger screens.
- Consistent alignment across navigation, hero, content sections, and footer.

### Spacing

Use a base spacing unit of 4px.

Recommended scale:

`4, 8, 12, 16, 24, 32, 48, 64, 96`

Use CSS custom properties to implement reusable spacing tokens.

### Layout Behavior

- Mobile-first responsive design.
- Single-column content on narrow screens.
- Multi-column layouts where screen space and content justify them.
- No horizontal overflow at the required viewport widths.
- Avoid unnecessary full-height sections or excessive empty space.

## 5. Page Composition

### Header

- Site identity: Inverting Entropy.
- Simple navigation to primary sections.
- Clear keyboard focus indicators.
- Mobile navigation should remain simple and accessible.
- A sticky header is optional, not required.

### Hero

The hero should contain:

- A short technical or thematic label.
- A clear professional headline.
- A concise description of technical focus.
- Primary action: View Projects.
- Secondary action: Contact or GitHub.
- A restrained computational visual element.

The hero must communicate the site's purpose without depending on animation.

### Professional Background

- Short, readable paragraphs.
- Emphasize technical experience and engineering approach.
- Avoid dense résumé-style formatting.
- Provide sufficient context to establish credibility.

### Technical Skills

- Group technologies by meaningful technical categories.
- Use simple lists, tags, or restrained cards.
- Avoid arbitrary proficiency percentages or unsupported rankings.

### Selected Projects

- Give projects visual prominence.
- Display the problem, technical approach, and outcome.
- Provide technologies and relevant links.
- Use consistent card or section layouts.
- Distinguish completed projects from work in progress.

### Contact and Footer

- Provide clear professional contact options.
- Keep the footer visually understated.
- Avoid unnecessary social media widgets or tracking integrations.

## 6. Computational Visual Language

The visual identity should suggest the transformation of disorder into structure.

### Preferred Motifs

- Particle fields converging into organized patterns.
- Fine geometric grids.
- Node-and-edge networks.
- Mathematical curves or structured point distributions.
- Subtle coordinate and indexing details.

### Initial Implementation

For the MVP, use a static SVG or CSS-based geometric composition in the hero.

The composition should:

- Be visually subordinate to the headline.
- Use the established color palette.
- Scale responsively.
- Avoid interfering with text or controls.
- Be decorative and hidden from assistive technology when it conveys no essential information.
- Require no external visualization library.

### Future Animation

Animation is optional and requires separate approval.

If introduced, it should:

- Support `prefers-reduced-motion`.
- Avoid distracting continuous motion.
- Respect performance constraints.
- Have a meaningful design purpose.
- Preserve a useful static presentation when disabled.

Do not implement a particle engine, canvas animation system, or third-party graphics dependency for the MVP without approval.

## 7. Components and Interaction

### Buttons and Links

- Primary actions use the accent color.
- Secondary actions use a restrained outline or text treatment.
- Interactive states must be visually distinguishable.
- Focus indicators must be clearly visible.
- Touch targets should meet applicable WCAG 2.2 sizing requirements.

### Cards

- Use surface colors and subtle borders.
- Keep decoration minimal.
- Avoid unnecessary shadows and glassmorphism.
- Maintain consistent internal spacing.

### Motion and Feedback

- Use restrained transitions for hover and focus states where appropriate.
- Essential feedback must not depend on animation.
- Avoid layout shifts caused by interaction.

## 8. Accessibility and Performance

The design must satisfy the applicable accessibility and performance requirements in `docs/requirements.md`.

Additional design expectations:

- Maintain readable text against all backgrounds.
- Avoid placing essential information inside decorative graphics.
- Preserve logical reading order when layouts change.
- Support browser zoom and text resizing.
- Avoid unnecessary font, image, and JavaScript downloads.
- Verify design behavior at 320, 375, 768, and 1440 CSS pixels.

## 9. Design Deliverables

Before implementation is considered complete:

- The color and typography tokens are implemented consistently.
- Responsive layouts are verified.
- The hero contains an approved computational visual.
- Navigation and interactive states are accessible.
- The project presentation is consistent.
- Browser screenshots are reviewed at representative viewport sizes.
- Visual deviations from this specification are documented.

## 10. Open Design Decisions

| ID | Decision | Status |
|---|---|---|
| DES-01 | Final hero headline and supporting copy | Open |
| DES-02 | Exact computational SVG composition | Open |
| DES-03 | Project card content and presentation | Open |
| DES-04 | Use of portrait or personal photography | Open |
| DES-05 | Final mobile navigation treatment | Open |

These decisions should be resolved during design review or through focused implementation tasks, rather than guessed by a coding agent.

## 11. Design Review Criteria

The design is acceptable when:

1. The site clearly communicates a professional AI/ML and software engineering identity.
2. Visitors can quickly find projects, skills, and contact information.
3. Computational visuals reinforce rather than obscure content.
4. The interface remains usable without JavaScript.
5. The design is responsive and accessible.
6. The implementation follows approved requirements and technology constraints.
7. The human developer has reviewed the rendered result.
