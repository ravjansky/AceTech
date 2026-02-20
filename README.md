# ⚡ AceTech Repair & Phone Accessories

> Precision device repair — micro-soldering, board-level diagnostics, LCD resurrection.  
> Olongapo City's go-to specialist for the repairs other shops won't touch.

A cyber-industrial single-page application built for [Acetech Repair and Phones Accessories](https://www.facebook.com/Acetech07), located at **104 Rizal Avenue Extension, East Tapinac, Olongapo City, Zambales, Philippines**.

---

## 🖥️ Preview

<!-- Replace with actual screenshot when available -->
<!-- ![AceTech Hero](./assets/screenshots/hero.png) -->

**Live site:** _Coming soon_

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| Markup | Semantic HTML5 — single-file SPA |
| Styling | Vanilla CSS — mobile-first, fluid `clamp()` typography |
| Animation | [GSAP](https://gsap.com) + [ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger/) |
| Smooth Scroll | [Lenis](https://lenis.darkroom.engineering/) synced to GSAP's RAF loop |
| Canvas | Vanilla JS — 3D wireframe grid (hero), no Three.js overhead |
| Typography | Custom Aero font (`woff2`) + JetBrains Mono fallback |
| Images | AVIF-optimized with `loading="lazy"` throughout |

**Zero frameworks. Zero build tools. One HTML file.**

---

## 📐 Architecture

The site is structured as a **3-page SPA** with client-side routing via `data-nav` attributes. Page transitions use a 10×10 **Glitch Grid** overlay — staggered red/black cell flicker powered by GSAP (~800ms in, ~400ms out).

```
index.html
├── Page 1 — Conversion Funnel
│   ├── Hero (canvas wireframe bg + char-by-char headline reveal)
│   ├── Trust Strip (infinite marquee loop)
│   ├── Services Grid (4 categories, scanline hover FX)
│   ├── Why Acetech (terminal-style bio card, blinking [ACTIVE] status)
│   ├── Social Proof (FB embed previews, inverted color filter)
│   └── CTA Strip (geo-service local SEO text)
│
├── Page 2 — Repair Hub
│   ├── Bento Grid (3-col → horizontal scroll-snap on mobile)
│   └── Portfolio Masonry (FB embeds)
│
└── Page 3 — Intel
    ├── Ace's Story
    ├── JSON-LD Terminal (syntax-highlighted typewriter on scroll)
    └── Google Maps (grayscale invert filter)
```

---

## ✨ Key Features

### Animations & Interactions
- **Boot Loader** — CSS-only chevron animation, no JS dependency
- **Menu Morph** — GSAP squash-stretch circle morph (hamburger → close)
- **Crosshair Cursor** — SVG turbulence `feDisplacementMap` glitch on hover
- **ScrollTrigger Reveals** — staggered fade-ups across all sections
- **Char-by-char Hero** — headline splits into individual spans, each animated in sequence
- **Terminal Typewriter** — JSON-LD schema rendered character-by-character with syntax highlighting

### Performance
- `transform` and `opacity` only — no layout thrashing
- `force3D: true` on GSAP tweens for GPU compositing
- Canvas particle count capped at 50 for mobile
- JS-based device detection to strip heavy animations on mobile before render
- `loading="lazy"` on all iframes and off-screen images
- `prefers-reduced-motion` respected via GSAP `matchMedia`

### SEO & Accessibility
- Semantic heading hierarchy (`h1` → `h3`)
- JSON-LD structured data in `<head>`
- Open Graph + meta description tags
- ARIA labels on navigation, overlays, and interactive elements
- Geo-service keywords for local search (Olongapo, Subic, Zambales)

---

## 🚀 Getting Started

No build step. Just serve it.

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/acetech-repair.git
cd acetech-repair

# Option 1: VS Code Live Server
# Right-click index.html → Open with Live Server

# Option 2: Python
python3 -m http.server 3000

# Option 3: Node
npx serve .
```

### Font Setup

Drop your `Aero` font files into `/assets/fonts/`:

```
assets/fonts/
├── Aero-Regular.woff2
└── Aero-Bold.woff2
```

The `@font-face` declarations are already in the CSS — they'll pick up the files automatically and fall back to JetBrains Mono (loaded via CDN) until the custom font is available.

---

## 📁 Project Structure

```
acetech-repair/
├── index.html              # The entire SPA — markup, styles, scripts
├── assets/
│   ├── fonts/              # Custom Aero .woff2 files
│   ├── images/             # AVIF-optimized photos
│   └── screenshots/        # README preview images
├── .gitignore
└── README.md
```

---

## 📝 Notes

- The **Google Maps embed** uses a placeholder `pb=` parameter. Replace it with the actual embed URL from [Google Maps](https://www.google.com/maps) for Acetech's listing.
- **Facebook embeds** use `invert(1) hue-rotate(180deg)` CSS filters to match the dark theme. These pull from the live [Acetech Facebook page](https://www.facebook.com/Acetech07).
- The crosshair cursor is desktop-only — hidden on touch devices via JS detection.

---

## 👤 Credits

**Client:** Ace — Acetech Repair and Phones Accessories  
**Developer:** [RavDigitals](https://github.com/YOUR_USERNAME)

---

<p align="center">
  <sub>Built with precision. Zero frameworks. Just craft.</sub>
</p>