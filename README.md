# Build Your Own Data Analyst Portfolio Website

A step-by-step guide to creating a professional, single-page portfolio website — no frameworks, no build tools, just one HTML file you can deploy anywhere.

This template was built for [Tobiloba Babajide](https://tobiloba-babajide.netlify.app/), a Data & BI Analyst and Tableau Ambassador. You can use it as a starting point and customize it for any profession.

---

## What You Get

A single `portfolio.html` file that includes:

- **Fixed navigation** with scroll-spy (active tab highlights as you scroll)
- **Hamburger menu** on mobile with animated toggle and auto-close on tap
- **Hero section** with photo, headline, stat cards, and action links
- **Experience timeline** with role descriptions and skill tags
- **Skills grid** organized by category with text-based icons
- **Education & Certifications** with numbered entries
- **Project portfolio** with tags and live links
- **Community & Teaching** highlights
- **Contact CTA** with email, CV, and social links
- **Custom favicon** generated from your initials
- **Dark theme** with CSS variables for easy recoloring
- **Fully responsive** — works on desktop, tablet, and mobile
- **No emojis** — uses clean text labels for maximum compatibility

No dependencies. No JavaScript frameworks. No build step.

---

## Quick Start

1. Download `portfolio.html`
2. Rename it to `index.html`
3. Open it in any text editor (VS Code, Sublime, Notepad++, or even Notepad)
4. Replace the content with your own information (see the section-by-section guide below)
5. Deploy (see Deployment section)

---

## File Structure

Everything lives in one HTML file with three parts:

```
index.html
├── <head>
│   ├── Google Fonts (DM Serif Display + Outfit)
│   ├── Favicon (inline SVG — your initials)
│   └── <style> (all CSS, ~500 lines)
│
├── <body>
│   ├── <nav>              — Fixed top navigation + hamburger menu
│   ├── #about             — Hero section (photo, headline, stats, links)
│   ├── #experience        — Work history timeline
│   ├── #skills            — Technical skills grid (3 columns)
│   ├── #certifications    — Education & certifications (2 columns)
│   ├── #portfolio         — Project cards (4 columns desktop)
│   ├── #community         — Community & teaching (2 columns)
│   ├── #contact           — Call-to-action box
│   └── <footer>
│
└── <script>               — Scroll-spy (~30 lines of vanilla JS)
```

---

## Section-by-Section Customization Guide

### 1. Page Title & Favicon

Find this near the top of the file:

```html
<title>Tobiloba Babajide — Portfolio</title>
```

Replace with your name. For the favicon, find the `<link rel="icon"...>` tag and change the two instances of `TB` to your own initials. The favicon colors come from the gradient — change `%233b82f6` (blue) and `%238b5cf6` (purple) to your preferred hex colors (replace `#` with `%23`).

### 2. Navigation

```html
<ul class="nav-links" id="navLinks">
  <li><a href="#about">About</a></li>
  <li><a href="#experience">Experience</a></li>
  <li><a href="#skills">Skills</a></li>
  <li><a href="#portfolio">Portfolio</a></li>
  <li><a href="#community">Community</a></li>
  <li><a href="#contact">Contact</a></li>
</ul>
```

Add, remove, or rename tabs as needed. Just make sure each `href="#id"` matches a `<section id="id">` in the page. The scroll-spy script picks these up automatically.

Each nav link also has an inline `onclick` handler that closes the mobile hamburger menu when a link is tapped. If you add a new link, copy the `onclick` from an existing one.

**Tip:** If you don't have a community/teaching section, just delete both the nav link and the section.

### 3. Hero Section

This is the first thing visitors see. Customize:

**Your badge** (the small label above your name):
```html
<div class="hero-badge">Tableau Community Leader</div>
```

**Your name:**
```html
<h1>Tobiloba<br><span>Babajide</span></h1>
```
The `<span>` part gets the gradient color.

**Your subtitle:**
```html
<p class="hero-subtitle">I'm a Data & BI Analyst who transforms...</p>
```

**Your action links:**
```html
<div class="hero-links">
  <a href="mailto:you@email.com" class="hero-link primary">Get in Touch</a>
  <a href="YOUR_CV_LINK" class="hero-link" target="_blank">View CV</a>
  <a href="YOUR_LINKEDIN" class="hero-link" target="_blank">LinkedIn</a>
  <!-- Add or remove links as needed -->
</div>
```
The first link with `class="hero-link primary"` gets the gradient background. All others are outlined.

**Your photo:**

Find the `<img class="hero-photo"` tag. Replace the `src` value with either:
- A base64-encoded image: `src="data:image/png;base64,YOUR_BASE64_STRING"`
- A hosted image URL: `src="https://your-domain.com/photo.jpg"`

To convert an image to base64 (Mac/Linux terminal):
```bash
base64 -w 0 your-photo.png
```

On Windows (PowerShell):
```powershell
[Convert]::ToBase64String([IO.File]::ReadAllBytes("your-photo.png"))
```

**Your stats:**
```html
<div class="stat-card">
  <div class="stat-number">3+</div>
  <div class="stat-label">Years Experience</div>
</div>
```
Change the numbers and labels. Add or remove stat cards (keep them in pairs for the 2-column grid).

**Mobile layout note:** On screens under 768px, the hero displays your name and subtitle first, with the photo and stat cards stacking below. On desktop, the photo sits to the right.

### 4. Experience Timeline

Each role follows this pattern:

```html
<div class="timeline-item">
  <div class="timeline-date">Jan 2025 — Present</div>
  <div class="timeline-content">
    <h3>Company Name</h3>
    <div class="timeline-role">Your Job Title</div>
    <p class="timeline-desc">What you did there, written in first person...</p>
    <div class="timeline-tags">
      <span class="tag">Skill 1</span>
      <span class="tag">Skill 2</span>
    </div>
  </div>
</div>
```

Copy and paste this block for each role. Most recent first.

### 5. Skills Grid

Each skill category is a card. The icon is a short text label inside a styled box — no emojis:

```html
<div class="skill-group">
  <div class="skill-group-icon">BI</div>
  <h3>Category Name</h3>
  <div class="skill-list">
    <span class="skill-tag">Skill 1</span>
    <span class="skill-tag">Skill 2</span>
  </div>
</div>
```

The template uses labels like `BI`, `DB`, `Py`, `XL`, `AI`, and `+`. Replace these with whatever short label fits your categories (e.g., `ML`, `UX`, `PM`).

The grid displays 3 columns on desktop, 2 on tablet, 1 on mobile. Add as many categories and skills as you need.

### 6. Education & Certifications

Each entry is numbered:

```html
<div class="cert-item">
  <div class="cert-number">1</div>
  <div>
    <div class="cert-name">Your Degree or Certification</div>
    <div class="cert-issuer">Institution - Date</div>
  </div>
</div>
```

Number them sequentially. The grid displays 2 columns on desktop, 1 on mobile.

### 7. Project Portfolio

Each project card:

```html
<a class="project-card" href="YOUR_PROJECT_URL" target="_blank">
  <div class="project-body">
    <div class="project-year">2025</div>
    <h3>Project Title</h3>
    <div class="project-tags">
      <span class="project-tag">Tag 1</span>
      <span class="project-tag">Tag 2</span>
    </div>
    <p>Short description of the project...</p>
    <span class="project-link-hint">View Project &rarr;</span>
  </div>
</a>
```

The grid displays 4 columns on desktop, 2 on tablet, 1 on mobile.

**For Tableau users:** You can link to Tableau Public vizzes using:
```
https://public.tableau.com/app/profile/YOUR_USERNAME/viz/WORKBOOK_NAME/SHEET_NAME
```

The last card in the template links to a "View All" page with a Tableau logo SVG. Replace or remove this if you're not a Tableau user.

### 8. Community & Teaching

Each card:

```html
<div class="community-card">
  <div class="highlight-tag">Label</div>
  <h3>Title</h3>
  <p>Description...</p>
</div>
```

If you don't have community involvement to showcase, delete this entire section and its nav link.

### 9. Contact CTA

Update the links at the bottom:

```html
<div class="cta-links">
  <a href="mailto:you@email.com" class="hero-link primary">Send Me an Email</a>
  <a href="YOUR_CV" class="hero-link" target="_blank">View CV</a>
  <a href="YOUR_LINKEDIN" class="hero-link" target="_blank">LinkedIn</a>
  <a href="YOUR_GITHUB" class="hero-link" target="_blank">GitHub</a>
</div>
```

### 10. Footer

```html
<footer>
  <div class="container">
    Your Name &middot; Your Title &middot; Your Location
  </div>
</footer>
```

---

## Changing the Color Theme

All colors are defined as CSS variables at the top of the `<style>` block. Change them to rebrand the entire site in seconds:

```css
:root {
  --navy: #0a1628;           /* Page background */
  --deep-blue: #101d35;      /* Darker shade */
  --accent: #3b82f6;         /* Primary accent (blue) */
  --accent-glow: #60a5fa;    /* Lighter accent for hovers */
  --warm: #f59e0b;           /* Secondary accent (amber) */
  --warm-glow: #fbbf24;      /* Lighter warm accent */
  --surface: #141e33;        /* Card backgrounds */
  --text: #e2e8f0;           /* Main text color */
  --text-muted: #94a3b8;     /* Secondary text color */
  --border: rgba(59, 130, 246, 0.12);  /* Subtle borders */
  --gradient-accent: linear-gradient(135deg, #3b82f6, #8b5cf6);  /* Blue-purple gradient */
  --gradient-warm: linear-gradient(135deg, #f59e0b, #ef4444);     /* Amber-red gradient */
}
```

**Want a light theme?** Swap the dark/light values:
- `--navy` → `#ffffff` or `#f8fafc`
- `--surface` → `#f1f5f9`
- `--text` → `#1e293b`
- `--text-muted` → `#64748b`
- `--border` → `rgba(0, 0, 0, 0.08)`

**Want a green theme?** Change the accent:
- `--accent` → `#10b981`
- `--accent-glow` → `#34d399`
- `--gradient-accent` → `linear-gradient(135deg, #10b981, #06b6d4)`

---

## Changing Fonts

The template uses two Google Fonts:

- **DM Serif Display** — for headings and large numbers (serif, elegant)
- **Outfit** — for body text (sans-serif, modern)

To change them, update the Google Fonts `<link>` tag in the `<head>` and the `font-family` declarations in the CSS:

```html
<link href="https://fonts.googleapis.com/css2?family=YOUR_SERIF_FONT&family=YOUR_SANS_FONT:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

Then find-and-replace:
- `'DM Serif Display', serif` → your serif font
- `'Outfit', sans-serif` → your sans-serif font

Good alternatives:
- Serif: Playfair Display, Lora, Merriweather, Source Serif Pro
- Sans-serif: Inter, Plus Jakarta Sans, Manrope, DM Sans

---

## Responsive Breakpoints

The template has two breakpoints:

| Screen Width | Layout |
|---|---|
| **> 1100px** | Full desktop — 4-col projects, 3-col skills, 2-col certs, side-by-side hero |
| **768px – 1100px** | Tablet — 2-col projects, 2-col skills |
| **< 768px** | Mobile — single column everything, hamburger menu, hero text above photo |

These are defined in the `@media` blocks near the bottom of the CSS.

On mobile, the hero section places your name and subtitle first (`order: 1`), with the photo and stat cards below (`order: 2`). The navigation collapses into a hamburger toggle that opens a full-width dropdown.

---

## How the Hamburger Menu Works

The `<button class="nav-toggle">` contains three `<span>` elements styled as horizontal bars. On click:

1. The button's `onclick` toggles the `.open` class on both itself and the `#navLinks` list
2. CSS transforms rotate the top and bottom bars into an X shape and fades the middle bar
3. The `.nav-links.open` rule switches the list from `display: none` to a vertical `flex` column positioned below the nav bar
4. Each nav link has its own `onclick` that removes `.open` from both elements, closing the menu after a tap

The hamburger is hidden on desktop (`display: none` above 768px) and only appears at the mobile breakpoint.

---

## How the Scroll-Spy Works

The `<script>` at the bottom of the file handles the active nav highlighting:

1. It reads all nav links and finds their matching `<section>` elements by ID
2. On every scroll event, it checks which section's top edge you've scrolled past (with a 120px offset for the fixed nav)
3. It adds the `.active` class to the matching nav link
4. Special case: when you're within 50px of the page bottom, it activates the last section (Contact) since it's too short to scroll past normally

If you add or remove sections, the script adapts automatically — just make sure your nav `href="#id"` values match your section `id` attributes.

---

## Deployment

### Option A: Netlify (recommended, free)

1. Create a folder with your `index.html` file
2. Go to [netlify.com](https://netlify.com) and sign up
3. Drag and drop your folder onto the Netlify dashboard
4. Your site is live at `your-name.netlify.app`
5. Optionally connect a custom domain

### Option B: GitHub Pages (free)

1. Create a new GitHub repository
2. Add your `index.html` to the root
3. Go to **Settings → Pages → Source** and select `main` branch
4. Your site is live at `your-username.github.io/repo-name`

### Option C: Vercel (free)

1. Push your `index.html` to a GitHub repo
2. Import it at [vercel.com](https://vercel.com)
3. Your site is live instantly

### Option D: Manual hosting

Upload `index.html` to any web server. It's a single file with no dependencies — it works anywhere.

---

## Checklist Before Publishing

- [ ] Replaced all placeholder text with your own content
- [ ] Updated your name in the title, hero, nav logo, and footer
- [ ] Added your photo (base64 or hosted URL)
- [ ] Updated the favicon initials
- [ ] Added your real email, LinkedIn, GitHub, and other links
- [ ] Added your CV/resume link
- [ ] Listed your actual work experience, skills, and certifications
- [ ] Added your real projects with live links
- [ ] Tested on mobile (resize your browser or use DevTools)
- [ ] Tested the hamburger menu opens and closes correctly
- [ ] Checked all external links work
- [ ] Removed any sections that don't apply to you

---

## Credits

Built with [Claude](https://claude.ai) by Anthropic. Designed for [Tobiloba Babajide](https://tobiloba-babajide.netlify.app/).

Fonts by [Google Fonts](https://fonts.google.com/). No external JavaScript libraries used.

---

## License

This template is free to use for personal and commercial projects. No attribution required, but appreciated.
