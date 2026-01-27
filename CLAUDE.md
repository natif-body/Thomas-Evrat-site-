# CLAUDE.md

Guide for AI assistants working on this repository.

## Project Overview

Single-page marketing website for **Thomas Evrat**, a personal sports coach based in Brignais (southwest Lyon, France). The site promotes at-home fitness coaching services under the brand **NATIF BODY**.

**Stack:** Pure HTML5, CSS3, and vanilla JavaScript. No build system, no frameworks, no package manager.

## File Structure

```
Thomas-Evrat-site-/
├── index.html                              # Main website (~1675 lines, single-page app)
├── README.md                               # Minimal project readme
├── CLAUDE.md                               # This file
├── Photo                                   # Placeholder file
├── services a la persone                   # Redirect/warning HTML page
└── Images/
    ├── 1.png, 2.png, 7.png                # PNG images (coach/branding)
    ├── 1.jpeg, 3.jpeg                      # JPEG images
    ├── 4.jpg, 5.jpg                        # JPEG images
    ├── Thomas-CoachLyon-HD09.jpg           # High-res photo (Canon EOS)
    └── Logo E.I. EVRAT (fond noir).PNG     # Business logo (dark background)
```

## Architecture

Everything lives in `index.html` — HTML structure, CSS styles, and JavaScript are all inline in one file. There are no external stylesheets or script files.

### HTML Sections (in order)

| Section ID       | Purpose                                    |
|------------------|--------------------------------------------|
| (header)         | Fixed navigation bar with logo and links   |
| (hero)           | Landing area with CTA buttons              |
| `#about`         | Coach biography and credentials            |
| `#prestations`   | 8 service offering cards                   |
| `#zones`         | Geographic coverage (16 municipalities)    |
| (advantages)     | Key selling points                         |
| `#avis`          | Client testimonials                        |
| `#tarifs`        | Pricing cards with tax credit details      |
| `#contact`       | Contact form and info                      |
| (footer)         | Footer with links and legal               |

### CSS Patterns

- **Color scheme:** Dark theme — black `#000`, white `#fff`, accent red `#e63946`
- **Layout:** CSS Grid and Flexbox
- **Spacing:** 8rem section padding (reduced on mobile)
- **Border radius:** Up to 25px for cards
- **Effects:** Box shadows, linear gradients, backdrop-filter blur
- **Responsive breakpoint:** 768px (single breakpoint for mobile)

Key CSS classes:
- `.cta-button` — Call-to-action buttons with hover animations
- `.prestation-card` — Service cards with gradient backgrounds
- `.tarif-card` — Pricing cards (`.popular` modifier for featured card)
- `.zone-tag` — Location tags with gradient styling
- `.gallery-item-masonry` — Image gallery items

### Animations

- `fadeInUp` — Bottom-to-top fade entrance
- `fadeIn` — Standard opacity fade
- `slideInLeft` / `slideInRight` — Lateral slide animations
- Smooth scroll via `html { scroll-behavior: smooth }`
- Cubic-bezier transitions for interactive hover effects

### JavaScript

Minimal vanilla JS handling:
- Mobile hamburger menu toggle (open/close with animation)
- Click-outside-to-close menu behavior
- Smooth scroll navigation to section anchors

## Development Workflow

### No build step required

Open `index.html` directly in a browser or serve with any static file server:
```bash
python3 -m http.server 8000
```

### Deployment

Static hosting — the site can be deployed to any static host (GitHub Pages, Netlify, Vercel, etc.) with no build configuration.

### Making changes

All edits happen in `index.html`. When modifying:
1. **CSS** is in the `<style>` block in `<head>`
2. **HTML content** is in the `<body>` sections
3. **JavaScript** is in the `<script>` block before `</body>`

## Conventions

### Language
- All user-facing content is in **French**
- Code comments (if any) and technical identifiers are in English
- Section IDs use French names: `prestations`, `avis`, `tarifs`, `zones`

### Naming
- CSS classes use camelCase: `heroContent`, `prestationCard`, `tarifCard`
- Section IDs use lowercase: `#about`, `#prestations`, `#contact`
- Image files use simple numeric names: `1.png`, `2.png`, etc.

### Accessibility
- `aria-label` on interactive elements (menu toggle)
- Semantic HTML5 elements: `<header>`, `<nav>`, `<section>`, `<footer>`
- Heading hierarchy: h1 > h2 > h3 > h4

### Responsive design
- Single breakpoint at 768px
- Mobile-first hamburger navigation
- Grid columns reduce on smaller screens
- Font sizes scale down for mobile

## Business Context

- **Coach:** Thomas Evrat, 9+ years experience, BPJEPS certified, Pilates certified
- **Brand:** NATIF BODY
- **Services:** 8 coaching disciplines (strength, health/wellness, weight loss, physical prep, stretching/pilates, postural, CrossTraining/HIIT, nutrition)
- **Pricing:** 39-300 EUR with 50% tax credit (services a la personne)
- **Coverage:** 16 municipalities around Brignais in southwest Lyon
- **Booking:** Calendly integration (thomas-evrat-coach/30min)
- **Contact:** thomas@evrat-coach.fr / 06 27 14 24 53

## Important Notes

- **Large images:** Several images exceed 1 MB (up to 4.9 MB). Consider optimizing if performance matters.
- **Single file:** All code is in one HTML file. For significant feature additions, consider extracting CSS/JS into separate files.
- **No dependencies:** Do not introduce npm, frameworks, or build tools without explicit request.
- **"services a la persone" file:** Contains a redirect/warning page — not part of the main site flow.
