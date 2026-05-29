# Portfolio Refresh — Design Spec

## Goal

Make eamonwoortman.github.io more appealing to recruiters hiring game developers. Optimize for the 5-second scan: who is this person, what do they do, how do I contact them.

## Constraints

- Work within the existing static WordPress export (no framework rebuild)
- Surgical HTML changes + CSS overrides only
- Ship with existing content (no new blog posts, projects, or resume)
- Keep the existing purple accent palette (#4527a4, #8344c5)
- Don't modify vendored WP assets in wp-content/ or wp-includes/

## Approach

Combined "Polish & Professional" + "Recruiter-Optimized" — CSS modernization across the board, plus targeted HTML restructuring of the hero and footer.

## Visual Direction

Dark Hero, Light Body — dark gradient hero section for dramatic first impression, transitioning to light background for the blog/project content below.

---

## Changes

### 1. Hero Section (HTML restructure)

**Replaces:** The current `wp-block-media-text` bio section (lines ~243–276 of index.html)

**New structure:**
- Full-width dark gradient container (`linear-gradient(135deg, #1a1a2e, #16213e)`)
- Left: circular profile photo (existing `20200118_131009_circle_1024_cropped.png`)
- Right: name, title ("Game Programmer"), condensed 1-2 line tagline
- Three CTA buttons:
  - **View Projects** — primary solid purple (#4527a4), links to /projects/
  - **Download Resume** — outlined purple, links to existing resume PDF
  - **Contact Me** — outlined purple, links to /contact/
- Tech skill badges row: Unity, C#, C++, Unreal Engine, Docker, CI/CD, Backend, Multiplayer
  - Styled as small rounded pills with semi-transparent purple background
- Gradient transition strip below hero fading into light body background
- Responsive: on mobile, photo stacks above text, buttons stack vertically

**What moves:**
- The multi-paragraph bio text moves below the hero (kept but deemphasized)
- Social icon links (LinkedIn, GitHub, GitLab, Docker Hub) move to the footer

**Dynamic years:** The existing `data-since` spans for dynamic year calculation are preserved in the bio text below the hero.

### 2. CSS Polish (style override block)

**Method:** Single `<style>` block injected into `<head>`, overriding OceanWP defaults. No changes to vendored CSS files.

**Typography:**
- Font stack: `system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`
- Applied to body, headings, and card text

**Spacing:**
- More generous padding on `#content-wrap` sections
- Consistent margins between blog/project card grids

**Card improvements:**
- Subtle hover effect: `transform: translateY(-2px)` + `box-shadow` on `.apbPost`
- Smooth transition: `transition: transform 0.2s, box-shadow 0.2s`
- Slightly more rounded corners on card borders

**Links:**
- Keep existing purple (#4527a4) for link color
- Add `transition: color 0.2s` for smoother hover states

**Mobile:**
- Hero flexbox switches to `flex-direction: column` below 768px
- CTA buttons wrap cleanly
- Tech badges wrap into multiple rows

### 3. Footer Redesign (HTML restructure)

**Replaces:** The current `#footer-widgets` (empty boxes) and `#footer-bottom` (generic OceanWP copyright)

**New structure:**
- Dark background matching hero (`#1a1a2e`)
- Three-column flex layout:
  - Left: "Eamon Woortman" + "Game Programmer"
  - Center: Social icons (LinkedIn, GitHub, GitLab, Docker Hub) using existing Font Awesome classes
  - Right: "© {year} Eamon Woortman" — year computed via the same inline JS pattern as the dynamic-years spans
- Icons use purple accent color (#a78bfa) with hover brightening

### 4. Header Navigation Polish (CSS only)

- Subtle bottom border on `#site-header` for visual separation
- Ensure nav link hover states use consistent purple accent
- No structural changes to the navigation HTML

---

## Files Modified

| File | Type of Change |
|------|---------------|
| `index.html` | Hero HTML restructure, footer HTML restructure, `<style>` block injection |

## Files NOT Modified

- `wp-content/**` — vendored theme/plugin assets
- `wp-includes/**` — vendored WP core assets
- `blog/index.html`, `projects/index.html`, `contact/index.html` — other pages unchanged
- Resume PDF — kept as-is

## Out of Scope

- New content (blog posts, projects, updated resume)
- Other pages beyond the homepage
- JavaScript beyond the existing dynamic-years script
- Build tooling, frameworks, or static site generators
- SEO or meta tag optimization
- Analytics integration
