# PRD: Graphite & Ember CSS Styling

## Introduction

`index.html` has approved semantic HTML and content, but no styling. It renders with browser defaults. This feature adds the Graphite & Ember visual design described in `docs/design.md`, which is the authoritative visual specification. That means one local stylesheet with design tokens, typography, a responsive layout, styled components (header, hero, skills, project cards, contact, footer), and accessible interaction states.

The work uses CSS only. It adds no JavaScript, dependencies, build tools, web fonts, or remote assets, consistent with the Project Rules in `AGENTS.md`. The hero's computational SVG artwork (DES-02) is **out of scope** and will get its own PRD. This PRD only makes sure the hero layout can accept that artwork later.

Related project requirements (`docs/requirements.md`): FR-01, FR-02, FR-04, FR-05, FR-07, FR-08, NFR-01, NFR-02, NFR-04, NFR-07.

## Goals

- Implement every approved Graphite & Ember color, typography, and spacing token as a CSS custom property in one place.
- Make the page readable and usable, with no layout-caused horizontal scrolling, at 320, 375, 768, and 1440 CSS pixels.
- Meet WCAG 2.2 AA for text contrast, non-text contrast of controls, visible focus, focus not obscured, and target size.
- Give projects visual prominence and make each project's lifecycle status easy to scan without relying on color.
- Keep the stylesheet small, organized, and understandable to a developer learning CSS.

## User Stories

Stories are listed in dependency order. "Typecheck passes" and "Verify in browser using dev-browser skill" have project-specific meanings, defined under Technical Considerations.

### US-001: Create the stylesheet and design tokens
**Description:** As a developer, I want all approved visual values defined once as CSS custom properties so that every component uses a consistent, auditable palette and scale.

**Acceptance Criteria:**
- [ ] `assets/css/styles.css` exists and is linked from the `<head>` of `index.html` with `<link rel="stylesheet" href="./assets/css/styles.css">`
- [ ] `:root` defines all ten color tokens from `docs/design.md` §2.2 with exactly those values
- [ ] `:root` defines spacing tokens `--space-1` through `--space-9` for 4, 8, 12, 16, 24, 32, 48, 64, 96 px (as `rem`)
- [ ] `:root` defines `--font-sans` and `--font-mono` using the stacks in `docs/design.md` §3
- [ ] `:root` defines type-scale tokens `--text-hero`, `--text-section`, `--text-card`, `--text-body`, `--text-supporting`, `--text-label` with the values in `docs/design.md` §3
- [ ] The stylesheet has the twelve labeled section comments, in the order given in `docs/architecture.md` §5
- [ ] No other changes to `index.html` besides the `<link>`
- [ ] Typecheck passes

### US-002: Base styles and typography
**Description:** As a visitor, I want comfortable, legible text on a dark graphite background so that I can read the content easily.

**Acceptance Criteria:**
- [ ] A minimal reset sets `box-sizing: border-box` on all elements and pseudo-elements and sets `body { margin: 0 }`
- [ ] `body` uses `--color-background`, `--color-text`, `--font-sans`, `--text-body`, and `line-height: 1.6`
- [ ] `h1`, `h2`, and `h3` use `--text-hero`, `--text-section`, and `--text-card` respectively, with `line-height` between 1.1 and 1.25
- [ ] Paragraphs have `max-width: 70ch`
- [ ] Links inside body text use `--color-accent` and `text-decoration: underline`. On hover, the underline thickness or offset changes (not just the color)
- [ ] All font sizes use `rem` or `clamp()`. There are no `px` font sizes
- [ ] No `@font-face` or `@import` rules exist
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill at 375 and 1440 CSS px

### US-003: Focus indicators and skip link
**Description:** As a keyboard user, I want a clearly visible focus indicator and a skip link so that I always know where I am and can bypass the navigation.

**Acceptance Criteria:**
- [ ] `:focus-visible` sets `outline: 3px solid var(--color-focus)` and a positive `outline-offset`
- [ ] The primary button focus style adds a contrasting inner ring (for example `box-shadow: 0 0 0 3px var(--color-background)`) so the amber outline is distinguishable from the amber fill. A CSS comment explains why
- [ ] The skip link (`a[href="#main"]` at the top of `body`) is visually hidden until focused. On focus it appears at the top-left with `--color-surface-elevated` background and `--color-text` text
- [ ] `main:focus` removes the outline only for `main` itself (it has `tabindex="-1"` and is not interactive)
- [ ] No other rule sets `outline: none` or `outline: 0`
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill: the first Tab press shows the skip link, Enter moves focus to `main`, and every following link shows an unclipped focus ring

### US-004: Page layout container and section rhythm
**Description:** As a visitor on any device, I want content aligned in a consistent, centered column with even spacing so that the page feels orderly and fits my screen.

**Acceptance Criteria:**
- [ ] A `.container` class sets `max-width: 1200px`, centers horizontally, and uses horizontal padding of `clamp(1.25rem, 4vw, 3rem)` (20px minimum)
- [ ] Header, each `main` section, and footer content are wrapped in or given the `.container` class
- [ ] Vertical spacing between sections uses `--space-8` or `--space-9`
- [ ] Only class attributes and wrapper `<div>` elements are added to `index.html`. The HTML check under Technical Considerations passes
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill at 320, 375, 768, and 1440 CSS px: `document.documentElement.scrollWidth <= window.innerWidth` at each width

### US-005: Header and navigation (static)
**Description:** As a visitor, I want a clear site identity and simple navigation at the top of the page so that I can jump to any section.

**Acceptance Criteria:**
- [ ] The header uses `position: static` (no `sticky` or `fixed`)
- [ ] The "Inverting Entropy" link uses `--text-card` or larger, bold, in `--color-text`, and still points to `#home`
- [ ] The nav list has no bullets or default padding and lays out its links with flexbox and `flex-wrap: wrap`, so all five links stay visible at 320 CSS px without JavaScript (fallback only; DES-05 stays open)
- [ ] Each nav link has `min-height: 44px` and enough horizontal padding for a target of at least 24 CSS px wide
- [ ] Nav links have a hover style that changes something other than color (for example an underline)
- [ ] The header has a `1px solid var(--color-border)` bottom border (decorative)
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill at 320, 375, 768, and 1440 CSS px; all five nav links are visible and reachable by Tab

### US-006: Hero section
**Description:** As a recruiter landing on the page, I want a clear headline and obvious next actions so that I understand the site's focus without scrolling.

**Acceptance Criteria:**
- [ ] The eyebrow paragraph ("Data Scientist and AI/ML Engineer") has a class and uses `--font-mono`, `--text-label`, `--color-accent`, and uppercase letter-spaced text
- [ ] `h1` uses `--text-hero` and `overflow-wrap: break-word`
- [ ] The description paragraph uses `--color-text-muted`
- [ ] The two CTA paragraphs are replaced by a single `<div class="hero-actions">` containing both links. Link text and `href` values are unchanged, and the HTML check passes
- [ ] "View Projects" has class `button button--primary`: `--color-accent` background, `--color-on-accent` text, no underline, and a hover state that changes background or border
- [ ] "Contact" has class `button button--secondary`: transparent background, `--color-text` text, and a `2px solid var(--color-accent)` border
- [ ] `.button` has `min-height: 44px`, `display: inline-flex`, `align-items: center`, and `white-space: nowrap`
- [ ] At `min-width: 64em` the hero uses a two-column CSS grid where text occupies the first column and the second column is reserved for future artwork. No placeholder element or SVG is added
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill at 320, 375, 768, and 1440 CSS px; at 1440×900 the headline and both buttons are visible without scrolling

### US-007: Professional Background section
**Description:** As a visitor, I want the background section to read as short, comfortable paragraphs so that it doesn't feel like a dense résumé.

**Acceptance Criteria:**
- [ ] `#about` paragraphs inherit the 70ch measure and are separated by `--space-4` or `--space-5`
- [ ] The `#about` heading and paragraphs align with the `.container` left edge
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill at 375 and 1440 CSS px

### US-008: Technical Skills section
**Description:** As a recruiter, I want skills grouped by category in a scannable layout so that I can quickly find relevant technologies.

**Acceptance Criteria:**
- [ ] Each `h3` plus its following `ul` in `#skills` is wrapped in a `<div class="skill-group">`. The HTML check passes
- [ ] The groups' parent uses `display: grid` with `grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr))` and a `--space-5` or `--space-6` gap
- [ ] `.skill-group` uses `--color-surface` background, `1px solid var(--color-border)` border, and `--space-5` padding
- [ ] `.skill-group h3` uses `--font-mono`, `--text-supporting`, and `--color-accent`
- [ ] No proficiency bars, percentages, or rankings are added
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill at 320, 375, 768, and 1440 CSS px; groups are one column at 320 and multiple columns at 1440

### US-009: Selected Projects cards
**Description:** As a hiring manager, I want each project in a consistent, prominent card with its employer and status easy to spot so that I can quickly judge the work and its maturity.

**Acceptance Criteria:**
- [ ] Each `#projects article` uses `--color-surface` background, `1px solid var(--color-border)` border, `--space-6` padding, and no `box-shadow` or `backdrop-filter`
- [ ] Cards stack in a single column at all widths, with `--space-6` between cards. A CSS comment explains that one column keeps the long descriptions readable
- [ ] The employer paragraph has class `project-employer` and uses `--color-text-muted` and `--text-supporting`
- [ ] The status paragraph has class `project-status` and uses `--font-mono` and `--text-label`. Its text is unchanged, so status is never conveyed by color alone. No new colors are added
- [ ] The section intro paragraph uses `--color-text-muted`
- [ ] The HTML check passes
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill at 320, 375, 768, and 1440 CSS px

### US-010: Contact section and footer
**Description:** As a visitor, I want clear professional links and an understated footer so that I know how to follow up.

**Acceptance Criteria:**
- [ ] The `#contact` list has no bullets. The GitHub and LinkedIn links use `--color-accent`, are underlined, and have `min-height: 44px` hit areas (via `display: inline-flex` or padding)
- [ ] The development placeholder paragraph uses `--color-text-muted` and is not hidden (`display`, `visibility`, and `opacity` unchanged)
- [ ] The footer uses `--color-text-muted`, `--text-supporting`, and a `1px solid var(--color-border)` top border
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill at 320 and 1440 CSS px; the footer does not overlap content

### US-011: Interaction transitions and reduced motion
**Description:** As a visitor sensitive to motion, I want any interface transitions to respect my reduced-motion preference.

**Acceptance Criteria:**
- [ ] Any `transition` lasts 200ms or less and only lists `color`, `background-color`, `border-color`, `outline-color`, `text-decoration-color`, or `box-shadow`
- [ ] `scroll-behavior: smooth` appears only inside `@media (prefers-reduced-motion: no-preference)`
- [ ] A `@media (prefers-reduced-motion: reduce)` block sets `transition: none` on all elements
- [ ] There are no `@keyframes` or `animation` rules
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill with `prefers-reduced-motion: reduce` emulated; hover states change instantly

### US-012: Contrast and responsive verification record
**Description:** As the project owner, I want a recorded verification of the finished styling so that I can review it before merging.

**Acceptance Criteria:**
- [ ] Every text color / background color pair used in `styles.css` is listed in `progress.txt` with a contrast ratio computed using the WCAG relative-luminance formula (for example, a Python calculation)
- [ ] Every listed pair is at least 4.5:1, or at least 3:1 for large text (≥ 24px, or ≥ 18.66px bold)
- [ ] Every border or outline that identifies an interactive control is at least 3:1 against its adjacent background, and the ratio is recorded
- [ ] Any pair that fails is fixed in `styles.css` using approved tokens only
- [ ] Typecheck passes
- [ ] Verify in browser using dev-browser skill at 320, 375, 768, and 1440 CSS px and at 200% zoom: no horizontal overflow, no clipped text, and a full Tab / Shift+Tab pass reaches every link with a visible focus ring

### US-013: Documentation synchronization
**Description:** As the project owner, I want the docs to reflect what was actually built so that the repository stays trustworthy.

**Acceptance Criteria:**
- [ ] `README.md` Project Status lists the stylesheet as "implemented, pending review" (not complete or deployed), and Repository Structure includes `assets/css/styles.css`
- [ ] The `docs/architecture.md` current-status line mentions the stylesheet. Architectural decisions are unchanged
- [ ] `docs/design.md` records the implemented refinements: focus inner ring on amber buttons, single-column project cards, static header, and wrapping nav fallback. Color tokens and specs are unchanged, and DES-05 stays open
- [ ] `docs/requirements.md` acceptance criteria are unchanged. FR-08 is not marked complete, because the hero visual (DES-02) is outstanding
- [ ] Commit uses the `docs:` prefix
- [ ] Typecheck passes

## Functional Requirements

- FR-1: The site must load exactly one local stylesheet, `assets/css/styles.css`, through a relative path. It must load no remote CSS, fonts, or scripts.
- FR-2: All colors in the stylesheet must reference the approved tokens from `docs/design.md` §2.2. No other colors may be introduced, except `transparent` and `currentColor`.
- FR-3: Spacing, font families, and font sizes must use the defined tokens, except for one-off structural values such as the 1200px max width or breakpoint widths.
- FR-4: The layout must be mobile-first. Base styles target narrow screens, and `min-width` media queries add multi-column layouts.
- FR-5: The header must be static. Navigation must work with no JavaScript at every required width.
- FR-6: The primary action ("View Projects") must use dark text on amber. The secondary action ("Contact") must use light text with an amber border.
- FR-7: Every interactive element must have a visible `:focus-visible` indicator that is not clipped, not obscured, and distinguishable from adjacent fills.
- FR-8: Body-text links must be distinguishable from surrounding text by an underline, not by color alone.
- FR-9: Project status must be presented as readable text with a distinct typographic treatment, not by color alone.
- FR-10: Changes to `index.html` are limited to the stylesheet `<link>`, class attributes, wrapper `<div>` elements, and the hero `.hero-actions` grouping. Visible text, `id` values, link `href` values, heading levels, and content order must not change.
- FR-11: Transitions must be disabled under `prefers-reduced-motion: reduce`.
- FR-12: The page must have no layout-caused horizontal scrolling at 320, 375, 768, and 1440 CSS pixels.

## Non-Goals

- No hero computational SVG artwork or placeholder graphic (DES-02); it will have a separate PRD.
- No final mobile navigation pattern such as a hamburger or disclosure menu (DES-05). Only the wrapping fallback is in scope.
- No sticky or fixed header.
- No JavaScript of any kind, including `assets/js/main.js`.
- No light mode or theme toggle.
- No web fonts, icon sets, CSS frameworks, preprocessors, linters, or build steps.
- No keyframe animations, particle effects, or scroll-triggered effects.
- No changes to page copy, project descriptions, or the contact mechanism (DEC-05).
- No portrait or photography (DEC-07 / DES-04).
- No deployment, `.nojekyll`, CI, or test framework.

## Design Considerations

- `docs/design.md` is authoritative. If this PRD and the design doc conflict, follow the design doc and record the conflict in `progress.txt`.
- Visual restraint: amber and orange are for accents, actions, and labels only. They must not be used for large background areas or body text.
- `--color-border` (#39434F) is decorative only. It fails 3:1 non-text contrast (1.36–1.63:1 against surfaces) and must never be the only visible boundary of an interactive control.
- Cards: surface color plus a subtle border, minimal decoration, and no heavy shadows.
- Breakpoints: base (< 768), `min-width: 48em` (768), and `min-width: 64em` (1024).

## Technical Considerations

### Ralph execution

- Branch: `ralph/css-styling`, created from `main`. The Ralph configuration (`AGENTS.md`, `scripts/ralph/`) must be merged into `main` first. Otherwise the new branch will not contain it.
- Local preview: `python3 -m http.server 8000 --bind 127.0.0.1` from the repository root, then open `http://127.0.0.1:8000`.

### "Typecheck passes" for this project

This is a static HTML/CSS site with no type checker or linter, and `AGENTS.md` forbids adding one. For this PRD, "Typecheck passes" means all of the following commands, run from the repository root, succeed:

1. **CSS check:** balanced braces, and no hex colors outside the `:root` token block. Run from US-001 onward.
   ```bash
   python3 -I -c "
   import re; s=open('assets/css/styles.css').read()
   assert s.count('{')==s.count('}'), 'unbalanced braces'
   i=s.index(':root'); j=s.index('}',i)
   bad=re.findall(r'#[0-9A-Fa-f]{3,8}\b', s[:i]+s[j:]); assert not bad, bad
   print('css ok')"
   ```
2. **HTML check:** visible text, `id` values, and link `href` values are unchanged from `main` (FR-10).
   ```bash
   python3 -I -c "
   import html.parser,subprocess
   class P(html.parser.HTMLParser):
       def __init__(s): super().__init__(); s.t=[]
       def handle_starttag(s,tag,a): s.t+=[v for k,v in a if k=='id' or (tag=='a' and k=='href')]
       def handle_data(s,d):
           d=' '.join(d.split())
           if d: s.t.append(d)
   def ext(src): p=P(); p.feed(src); return p.t
   old=subprocess.run(['git','show','main:index.html'],capture_output=True,text=True,check=True).stdout
   assert ext(old)==ext(open('index.html').read()), 'visible text, ids, or hrefs changed'
   print('html ok')"
   ```
3. **No external assets or dependencies:** each of these prints nothing.
   ```bash
   grep -nE '<(link|script)[^>]*(href|src)="(https?:)?//' index.html
   grep -nE '@import|url\(["'\'']?(https?:)?//' assets/css/styles.css
   ls package.json package-lock.json node_modules 2>/dev/null
   ```

### "Verify in browser using dev-browser skill"

No dev-browser skill or browser tooling is currently installed, and installing it is not part of this PRD. If browser verification is unavailable in an iteration:

- Write `Manual browser verification needed: <the exact checks from the criterion>` in `progress.txt` and in the story's `notes` field in `prd.json`.
- Set `passes: true` only if every other criterion passed. The `notes` entry marks the story for human browser review before merge.
- Do not claim that browser checks passed unless they were actually performed.

### Additional contrast pairs

These were computed during PRD drafting and must be re-verified against the final CSS in US-012.

| Foreground | Background | Ratio |
|---|---|---:|
| `#F4F6F8` text | `#1B2028` surface | 15.10:1 |
| `#F4F6F8` text | `#272E38` elevated | 12.64:1 |
| `#AEB8C4` muted | `#272E38` elevated | 6.81:1 |
| `#FFB000` accent | `#1B2028` surface | 8.93:1 |
| `#FFB000` accent | `#272E38` elevated | 7.47:1 |
| `#FF683B` accent-2 | `#1B2028` surface | 5.68:1 |
| `#FF683B` accent-2 | `#272E38` elevated | 4.76:1 (normal text passes, but with little margin) |
| `#39434F` border | `#1B2028` / `#272E38` | 1.63:1 / 1.36:1 (decorative only) |

### Browser support

Current Chrome, Firefox, Safari, and Edge. `clamp()`, `:focus-visible`, CSS Grid, and custom properties are all supported there.

## Success Metrics

- All 13 stories reach `passes: true`, and the static checks pass on the final branch.
- Zero hex literals outside the token block, and zero colors outside the approved palette.
- No horizontal overflow and no clipped focus at any of the four required widths.
- The human developer reviews the rendered page at 320, 375, 768, and 1440 CSS px, including every story flagged "Manual browser verification needed", and approves it.
- The stylesheet stays under about 500 lines, with section comments.

## Open Questions

1. **DES-05 — Final mobile navigation treatment.** This PRD implements only a wrapping link-row fallback. Should the final pattern be that row, a CSS-only `<details>` disclosure, or something else?
2. **Skills presentation:** keep the current comma-separated list items, or split them into individual tag "chips"? Chips would change list content, which FR-10 currently forbids.
3. **Hero right column:** at ≥ 1024px, should the hero stay single-column until the SVG exists, instead of reserving an empty grid column?
4. **Browser verification tooling:** should a browser automation tool be approved later, so that Ralph iterations can perform the "Verify in browser" criteria themselves instead of deferring them to human review?
