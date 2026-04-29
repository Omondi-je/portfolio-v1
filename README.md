# Jeff Omondi — Portfolio v1

A single-file personal portfolio for a Data Scientist & Machine Learning Engineer. Built with vanilla HTML, CSS, and JavaScript — no build step required.

**File:** `jeff_omondi_portfolio.html`  
**Version:** v1 (see also: `jeff_omondi_portfolio_v2.html`)

---

## Overview

This is the original version of Jeff Omondi's portfolio. It shares the same content (projects, skills, tech stack, workflow) as v2 but uses a softer, space-themed aesthetic: a canvas starfield background, glassmorphism cards, horizontal skill bars, and CSS-driven scroll reveal animations — rather than v2's WebGL void, SVG skill rings, GSAP animations, and boot sequence.

---

## Sections

| Section | ID | Description |
|---|---|---|
| Navigation | `#navbar` | Fixed top bar, becomes opaque on scroll; collapses to hamburger on mobile |
| Hero | — | Name, typing animation cycling through job titles, CTA buttons |
| About | `#about` | Bio, animated stat counters (years exp, models deployed, datasets processed, accuracy) |
| Skills | `#skills` | 10 core skills with animated horizontal progress bars, filterable by category |
| Tech Stack | `#tech` | 57-item icon grid with 2-letter abbreviations, filterable by category |
| Projects | `#projects` | 6 project cards, filterable by category; click opens a detail modal |
| Workflow | `#workflow` | Alternating left-right timeline of Jeff's 7-step data science process |
| Contact | `#contact` | Email, GitHub, and LinkedIn cards + resume download button |
| Footer | — | Tagline and copyright |

---

## vs. Portfolio v2

| Feature | v1 (this file) | v2 |
|---|---|---|
| Background | Canvas starfield (vanilla JS) | WebGL particle scene |
| Skill display | Horizontal progress bars | SVG circular rings |
| Scroll animation | CSS `IntersectionObserver` reveal | GSAP + ScrollTrigger |
| Smooth scroll | Native CSS `scroll-behavior: smooth` | Lenis library |
| Boot sequence | ✗ | ✓ Simulated terminal on load |
| Custom cursor | ✗ | ✓ Glowing cursor with hover expansion |
| Terminal easter egg | ✗ | ✓ Press `` ` `` to open |
| Magnetic buttons | ✗ | ✓ |
| Film grain overlay | ✗ | ✓ |
| Tech stack display | Icon grid with 2-letter abbreviations | Tag cloud (text only) |
| Stat counters | ✓ Animated number count-up | ✓ |

The content (projects, skills, tech stack, workflow steps, contact links, GitHub URLs) is identical between both versions.

---

## Data

All content lives in a single `portfolioData` object in the `<script>` block (~line 582). Three arrays drive the page:

### `portfolioData.skills` — 10 entries

Each entry: `{ name, level, category }`

`level` is a percentage (0–100) used to animate the progress bar width. Categories: `languages`, `ml`, `engineering`, `mlops`, `viz`.

### `portfolioData.techStack` — 57 entries

Each entry: `{ name, category, icon }`

`icon` is a 2–3 character abbreviation displayed in the icon tile. Categories: `languages`, `python`, `engineering`, `mlops`, `viz`, `tools`.

### `portfolioData.projects` — 6 entries

Each entry: `{ id, title, category, domain, problem, dataset, tech[], methods[], results[], github, color }`

Color values (`"cyan"` | `"purple"` | `"pink"`) control the card accent stripe and badge colours via Tailwind dynamic classes.

### `portfolioData.workflow` — 7 steps

Each entry: `{ step, title, description }` — rendered into an alternating timeline.

---

## Projects

| # | Title | Domain | Key Result |
|---|---|---|---|
| 1 | Real-Time Fraud Detection System | Anomaly Detection / Financial | 95% precision, 50ms latency, 10K+ TPS |
| 2 | NLP Sentiment Analysis API | NLP / Social Media | 88% accuracy, 2K+ req/min |
| 3 | Computer Vision Inventory System | CV / Warehouse | 92% mAP, 80% time reduction |
| 4 | Customer Churn Prediction Pipeline | Classification / Telecom | 89% accuracy, 0.87 F1 |
| 5 | Sales Forecasting Engine | Time Series / Retail | 8.5% MAPE, 35% fewer stockouts |
| 6 | Recommendation Engine | Recommendations / E-commerce | +35% CTR, +28% conversion |

All GitHub links point to `https://github.com/Omondi-je/`.

---

## Tech Stack (portfolio itself)

| Dependency | Purpose |
|---|---|
| [Tailwind CSS](https://tailwindcss.com) (CDN) | Utility-class styling |
| [Google Fonts](https://fonts.google.com) | Orbitron, Rajdhani, Space Grotesk |
| Vanilla JS canvas | Starfield background animation |
| `IntersectionObserver` | Scroll-reveal for `.reveal` elements |

No Three.js, no GSAP, no Lenis. Everything except fonts is either CDN Tailwind or native browser APIs.

---

## Color Palette

| Variable | Value | Used for |
|---|---|---|
| `--space` | `#0a0a0f` | Background |
| `--cyan` | `#00d4ff` | Primary accent — links, skill bars, timeline, buttons |
| `--purple` | `#7c3aed` | Secondary accent — gradients, method badges |
| `--pink` | `#f472b6` | Tertiary accent — gradient text, LinkedIn card |

---

## Usage

Open directly in any modern browser — no server or install required:

```bash
open jeff_omondi_portfolio.html
```

---

## Customisation

All content is in the `portfolioData` object. To update:

- **Skills** — edit `level` (0–100) to change bar widths; update `category` to affect filter tabs
- **Tech stack** — add/remove entries; `icon` is the 2-char tile label
- **Projects** — add a new object to the `projects` array; valid `color` values are `"cyan"`, `"purple"`, `"pink"`
- **Workflow** — edit `portfolioData.workflow` step descriptions
- **Contact links** — update the `href` attributes in the `#contact` section HTML directly

To change the colour scheme, update the CSS variables in `:root` and the matching Tailwind `extend.colors` config at the top of the file.

---

## Browser Support

Requires a modern browser with support for CSS `backdrop-filter`, `IntersectionObserver`, and canvas 2D. Custom scrollbar styling is webkit-only (Chrome/Edge/Safari); Firefox uses the thin scrollbar fallback.# portfolio-v1
