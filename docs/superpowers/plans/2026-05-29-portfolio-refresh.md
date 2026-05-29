# Portfolio Refresh Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Refresh the eamonwoortman.github.io homepage for recruiter appeal — dark hero with CTAs, CSS modernization, professional footer.

**Architecture:** All changes are in a single file (`index.html`). We inject a `<style>` block for CSS overrides, replace the hero HTML region, and replace the footer HTML region. No vendored WP assets are touched.

**Tech Stack:** Static HTML, CSS, inline JS (existing dynamic-years pattern)

---

## File Map

| File | Action | Responsibility |
|------|--------|---------------|
| `index.html` | Modify | All changes: CSS `<style>` block injection, hero HTML replacement, footer HTML replacement, JS update for copyright year |

### Regions in index.html

| Region | Lines | Action |
|--------|-------|--------|
| `<head>` close | 72-73 | Inject new `<style>` block before `</head>` |
| Hero (wp-block-media-text) | 243-276 | Replace with dark gradient hero + deemphasized bio below |
| Footer (#footer-widgets + #footer-bottom) | 450-510 | Replace with new dark footer |
| Inline JS (bottom of body) | 551 | Extend to also set copyright year |

---

### Task 1: Inject CSS polish `<style>` block into `<head>`

**Files:**
- Modify: `index.html:72` (insert before `</head>`)

- [ ] **Step 1: Add the CSS override block**

Insert this `<style>` block immediately before line 72's `</head>`:

```html
<style id="portfolio-refresh-css">
/* === Portfolio Refresh: CSS Overrides === */

/* Typography */
body, .site-content, .entry, h1, h2, h3, h4, h5, h6,
.apbPostTitle a, .apbPostExcerpt, .apbPostMeta {
  font-family: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
}

/* Links */
a { transition: color 0.2s ease; }

/* Card hover effects */
.apbPost {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  border-radius: 8px;
  overflow: hidden;
}
.apbPost:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

/* Content spacing */
#content-wrap { padding-top: 2em; padding-bottom: 2em; }
.apbGridPosts { gap: 1.5em; }

/* Header polish */
#site-header {
  border-bottom: 1px solid rgba(0,0,0,0.08);
}
#site-header .menu-link:hover .text-wrap {
  color: #4527a4;
}

/* Hero section */
.portfolio-hero {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
  padding: 48px 24px;
  margin: -30px -30px 0 -30px;
}
.portfolio-hero-inner {
  display: flex;
  align-items: center;
  gap: 32px;
  max-width: 900px;
  margin: 0 auto;
}
.portfolio-hero-photo {
  flex-shrink: 0;
  width: 140px;
  height: 140px;
  border-radius: 50%;
  border: 3px solid rgba(167,139,250,0.3);
  object-fit: cover;
}
.portfolio-hero-text { color: #fff; }
.portfolio-hero-name {
  font-size: 2em;
  font-weight: 700;
  margin: 0 0 4px 0;
  line-height: 1.2;
}
.portfolio-hero-title {
  font-size: 1.1em;
  color: #a78bfa;
  font-weight: 500;
  margin: 0 0 8px 0;
}
.portfolio-hero-tagline {
  font-size: 0.95em;
  color: #94a3b8;
  margin: 0 0 16px 0;
  line-height: 1.5;
}
.portfolio-hero-ctas {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 16px;
}
.portfolio-hero-cta {
  display: inline-block;
  padding: 8px 20px;
  border-radius: 6px;
  font-size: 0.85em;
  font-weight: 600;
  text-decoration: none;
  transition: opacity 0.2s ease;
}
.portfolio-hero-cta:hover { opacity: 0.85; }
.portfolio-hero-cta--primary {
  background: #4527a4;
  color: #fff;
}
.portfolio-hero-cta--secondary {
  background: transparent;
  color: #a78bfa;
  border: 1px solid #a78bfa;
}
.portfolio-hero-badges {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}
.portfolio-hero-badge {
  background: rgba(69,39,164,0.25);
  color: #c4b5fd;
  padding: 4px 10px;
  border-radius: 4px;
  font-size: 0.75em;
}
.portfolio-hero-transition {
  height: 24px;
  background: linear-gradient(to bottom, #16213e, #f5f5f5);
  margin: 0 -30px;
}

/* Bio (deemphasized below hero) */
.portfolio-bio {
  max-width: 700px;
  margin: 2em auto;
  color: #555;
  font-size: 0.95em;
  line-height: 1.7;
}

/* New footer */
.portfolio-footer {
  background: #1a1a2e;
  padding: 24px 32px;
}
.portfolio-footer-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 900px;
  margin: 0 auto;
}
.portfolio-footer-brand { color: #fff; }
.portfolio-footer-name {
  font-weight: 600;
  font-size: 0.95em;
}
.portfolio-footer-role {
  color: #94a3b8;
  font-size: 0.8em;
  margin-top: 2px;
}
.portfolio-footer-social {
  display: flex;
  gap: 16px;
}
.portfolio-footer-social a {
  color: #a78bfa;
  font-size: 1.2em;
  transition: color 0.2s ease;
  text-decoration: none;
}
.portfolio-footer-social a:hover { color: #c4b5fd; }
.portfolio-footer-copyright {
  color: #64748b;
  font-size: 0.75em;
}

/* Mobile responsive */
@media (max-width: 768px) {
  .portfolio-hero { padding: 32px 16px; }
  .portfolio-hero-inner { flex-direction: column; text-align: center; }
  .portfolio-hero-ctas { justify-content: center; }
  .portfolio-hero-badges { justify-content: center; }
  .portfolio-footer-inner { flex-direction: column; gap: 16px; text-align: center; }
}
</style>
```

- [ ] **Step 2: Verify the style block is correctly placed**

Open `index.html` and confirm the new `<style id="portfolio-refresh-css">` appears directly before `</head>`, after the existing OceanWP CSS style block.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "style: inject CSS overrides for portfolio refresh

Typography (system font stack), card hover effects, link transitions,
hero/footer/bio styles, header polish, and mobile breakpoints."
```

---

### Task 2: Replace hero section with dark gradient hero

**Files:**
- Modify: `index.html:243-276` (replace the `wp-block-media-text` div)

- [ ] **Step 1: Replace the hero HTML**

Replace the entire block from `<div class="wp-block-media-text has-media-on-the-right...` (line 243) through the closing `</div>` on line 276 with:

```html
<div class="portfolio-hero">
  <div class="portfolio-hero-inner">
    <img src="https://eamonwoortman.github.io/wp-content/uploads/2020/04/20200118_131009_circle_1024_cropped.png"
         alt="Eamon Woortman" class="portfolio-hero-photo" width="140" height="140">
    <div class="portfolio-hero-text">
      <h1 class="portfolio-hero-name">Eamon Woortman</h1>
      <p class="portfolio-hero-title">Game Programmer</p>
      <p class="portfolio-hero-tagline">Versatile full-stack game developer with <span class="dynamic-years" data-since="2011"></span>+ years in game design, development &amp; integration — from gameplay to backend to CI/CD.</p>
      <div class="portfolio-hero-ctas">
        <a href="https://eamonwoortman.github.io/projects/" class="portfolio-hero-cta portfolio-hero-cta--primary">View Projects</a>
        <a href="https://eamonwoortman.github.io/wp-content/uploads/2017/02/eamon_woortman_resume.pdf" target="_blank" rel="noreferrer noopener" class="portfolio-hero-cta portfolio-hero-cta--secondary">Download Resume</a>
        <a href="https://eamonwoortman.github.io/contact/" class="portfolio-hero-cta portfolio-hero-cta--secondary">Contact Me</a>
      </div>
      <div class="portfolio-hero-badges">
        <span class="portfolio-hero-badge">Unity</span>
        <span class="portfolio-hero-badge">C#</span>
        <span class="portfolio-hero-badge">C++</span>
        <span class="portfolio-hero-badge">Unreal Engine</span>
        <span class="portfolio-hero-badge">Docker</span>
        <span class="portfolio-hero-badge">CI/CD</span>
        <span class="portfolio-hero-badge">Backend</span>
        <span class="portfolio-hero-badge">Multiplayer</span>
      </div>
    </div>
  </div>
</div>
<div class="portfolio-hero-transition"></div>

<div class="portfolio-bio">
  <p>I have vast experience and knowledge in front-to-back development including, but not limited to, gameplay programming, client and server programming, back-end development and continuous integration.</p>
  <p>Additionally, I&#8217;ve got more than <span class="dynamic-years" data-since="2005"></span> years of modding and programming experience in individual projects, as well as collaborative projects. I am driven to create fun games for the players which also stimulates online communities.</p>
  <p>On this blog you will find old and new <a href="https://eamonwoortman.github.io/projects/">projects</a> as well as <a href="https://eamonwoortman.github.io/blog/">blog posts</a> about several development subjects.</p>
</div>
```

Key changes from original:
- Profile photo moves to left of the hero text (was on the right in the media-text block)
- Bio condensed into hero tagline; full paragraphs moved to `.portfolio-bio` div below
- Social links removed from bio (they move to footer in Task 3)
- Resume link & contact link become CTA buttons
- "Greetings" greeting removed — the hero is the greeting now
- Dynamic years spans preserved (both 2011 and 2005 baselines)

- [ ] **Step 2: Verify hero renders correctly**

Open `index.html` in a browser. Confirm:
- Dark gradient hero with circular photo on the left
- Name, title, tagline, 3 CTA buttons, 8 tech badges visible
- Gradient transition strip fades to light background
- Bio paragraphs appear below in lighter style
- Dynamic years display correct numbers (15 and 21 for 2026)

- [ ] **Step 3: Verify mobile responsive**

Resize browser to < 768px. Confirm:
- Photo stacks above text (centered)
- CTA buttons and badges wrap
- No horizontal overflow

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: replace hero with dark gradient recruiter-optimized layout

Circular profile photo, name/title/tagline, 3 CTA buttons (View Projects,
Download Resume, Contact Me), 8 tech skill badges. Bio text deemphasized
below the hero. Social links removed (moving to footer next)."
```

---

### Task 3: Replace footer with professional dark footer

**Files:**
- Modify: `index.html:450-510` (replace `#footer-widgets` and `#footer-bottom`)

- [ ] **Step 1: Replace the footer HTML**

Replace everything from `<div id="footer-widgets"` (line 450) through `</div>\n<!-- #footer-bottom -->` (line 510) with:

```html
<div class="portfolio-footer">
  <div class="portfolio-footer-inner">
    <div class="portfolio-footer-brand">
      <div class="portfolio-footer-name">Eamon Woortman</div>
      <div class="portfolio-footer-role">Game Programmer</div>
    </div>
    <div class="portfolio-footer-social">
      <a href="https://www.linkedin.com/in/eamon-woortman/" target="_blank" rel="noreferrer noopener" aria-label="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
      <a href="https://github.com/eamonwoortman/" target="_blank" rel="noreferrer noopener" aria-label="GitHub"><i class="fab fa-github"></i></a>
      <a href="https://gitlab.com/eamon.woortman" target="_blank" rel="noreferrer noopener" aria-label="GitLab"><i class="fab fa-gitlab"></i></a>
      <a href="https://hub.docker.com/r/eamonwoortman/" target="_blank" rel="noreferrer noopener" aria-label="Docker Hub"><i class="fab fa-docker"></i></a>
    </div>
    <div class="portfolio-footer-copyright">
      &copy; <span id="copyright-year"></span> Eamon Woortman
    </div>
  </div>
</div>
```

- [ ] **Step 2: Update inline JS to set copyright year**

The existing inline JS at the bottom of the file is:

```js
document.querySelectorAll('.dynamic-years').forEach(function(el){el.textContent=new Date().getFullYear()-parseInt(el.dataset.since)});
```

Replace it with:

```js
document.querySelectorAll('.dynamic-years').forEach(function(el){el.textContent=new Date().getFullYear()-parseInt(el.dataset.since)});var cy=document.getElementById('copyright-year');if(cy)cy.textContent=new Date().getFullYear();
```

- [ ] **Step 3: Verify footer renders correctly**

Open `index.html` in a browser. Confirm:
- Dark footer with name/title on left, social icons in center, copyright on right
- Social icons are purple (#a78bfa) and brighten on hover
- Copyright year shows current year (2026)
- All social links open in new tabs to correct URLs

- [ ] **Step 4: Verify mobile responsive**

Resize browser to < 768px. Confirm:
- Footer stacks vertically (name, then icons, then copyright) — all centered

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: replace footer with professional dark layout

Dark background matching hero. Three-column layout: name/title,
social icons (LinkedIn, GitHub, GitLab, Docker Hub), dynamic
copyright year. Replaces empty WP widget boxes and generic
OceanWP copyright."
```

---

### Task 4: Final verification and cleanup

**Files:**
- Read: `index.html` (full review)

- [ ] **Step 1: Full page visual check**

Open `index.html` in a browser. Walk through top to bottom:
- Header nav renders cleanly with bottom border
- Dark hero with photo, name, title, tagline, CTAs, badges
- Gradient transition into light body
- Bio text below hero
- Blog posts section with card hover effects
- Projects section with card hover effects
- Dark footer with social icons and copyright

- [ ] **Step 2: Check all links work**

Click each of these and verify they navigate correctly:
- "View Projects" CTA → /projects/
- "Download Resume" CTA → opens resume PDF in new tab
- "Contact Me" CTA → /contact/
- Footer LinkedIn icon → linkedin.com/in/eamon-woortman/
- Footer GitHub icon → github.com/eamonwoortman/
- Footer GitLab icon → gitlab.com/eamon.woortman
- Footer Docker Hub icon → hub.docker.com/r/eamonwoortman/
- Nav links (Home, Blog, Projects, Contact)

- [ ] **Step 3: Mobile check at 375px and 768px widths**

Resize browser to both widths. Confirm:
- No horizontal overflow at either width
- Hero stacks vertically at 768px and below
- Footer stacks vertically at 768px and below
- CTA buttons and badges wrap cleanly
- Text is readable at both sizes

- [ ] **Step 4: Verify no vendored files were modified**

```bash
git diff --name-only
```

Expected: only `index.html` appears. No files under `wp-content/` or `wp-includes/`.

- [ ] **Step 5: Final commit if any fixes were needed**

Only if Steps 1-3 revealed issues that required fixes:

```bash
git add index.html
git commit -m "fix: address visual issues from final review"
```
