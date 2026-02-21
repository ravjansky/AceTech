<p align="center">
  <img src="acetech-logo.avif" alt="Acetech Repair Logo" height="60">
</p>

<h1 align="center">⚡ AceTech Repair & Phone Accessories</h1>

<p align="center">
  <strong>Precision device repair — micro-soldering, board-level diagnostics, LCD resurrection.</strong><br>
  Olongapo City's go-to specialist for the repairs other shops won't touch.
</p>

<p align="center">
  <a href="https://acetech-eby.pages.dev"><img src="https://img.shields.io/badge/🌐_Live_Site-acetech--eby.pages.dev-E11D2A?style=for-the-badge" alt="Live Site"></a>
  <a href="https://www.facebook.com/Acetech07"><img src="https://img.shields.io/badge/Facebook-Acetech07-1877F2?style=for-the-badge&logo=facebook&logoColor=white" alt="Facebook"></a>
</p>

---

## 🖥️ Preview

<p align="center">
  <img src="https://github.com/ravjansky/AceTech/raw/main/webclip.png" alt="AceTech Preview" width="200">
</p>

A **cyber-industrial single-page application** built for [Acetech Repair and Phones Accessories](https://www.facebook.com/Acetech07), located at **104 Rizal Avenue Extension, East Tapinac, Olongapo City, Zambales, Philippines**.

**🔗 Live at:** [acetech-eby.pages.dev](https://acetech-eby.pages.dev)

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Markup** | Semantic HTML5 — single-file SPA (`index.html`, ~117KB) |
| **Styling** | Vanilla CSS — fluid `clamp()` typography, CSS custom properties |
| **Animation** | [GSAP 3.12](https://gsap.com) + [ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger/) |
| **Smooth Scroll** | [Lenis 1.0](https://lenis.darkroom.engineering/) synced to GSAP's RAF loop |
| **3D Graphics** | Raw WebGL — custom GLSL shaders for hero gridscan (no Three.js) |
| **Canvas** | Vanilla JS — 3D particle system with perspective projection |
| **Typography** | Custom **Aero** font (`.ttf`) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) fallback |
| **Images** | AVIF-optimized with `loading="lazy"` throughout |
| **Hosting** | [Cloudflare Pages](https://pages.cloudflare.com/) |

> **Zero frameworks. Zero build tools. Zero dependencies. One HTML file.**

---

## 📐 Architecture

The site is a **3-page SPA** with client-side routing via `data-nav` attributes. Page transitions use a 10×10 **Glitch Grid** overlay — staggered red/black cell flicker powered by GSAP (~800ms in, ~400ms out).

```
index.html (single file — markup, CSS, JS)
│
├── Page 1 — HOME (Conversion Funnel)
│   ├── Hero Section
│   │   ├── WebGL Gridscan Background (custom GLSL fragment shader)
│   │   ├── Char-by-char Headline Animation (text splitting + GSAP stagger)
│   │   ├── Phone Glitch Mask Effect (canvas pixel-block reveal on hover)
│   │   └── 3D Particle Canvas (perspective-projected sphere with connections)
│   ├── Trust Strip (infinite CSS marquee loop)
│   ├── 3D Services Tunnel (CSS preserve-3d, scroll-driven z-axis navigation)
│   ├── Why Acetech (terminal-style bio card with live OPEN/CLOSED status)
│   ├── Social Proof (Facebook post embeds with grayscale → color hover)
│   └── CTA Strip (geo-service local SEO keywords)
│
├── Page 2 — REPAIR HUB
│   ├── Bento Grid (3-col responsive → horizontal scroll-snap on mobile)
│   ├── Repair Portfolio (Facebook embed masonry layout)
│   └── Facebook CTA Section
│
└── Page 3 — INTEL
    ├── Ace's Story (founder bio)
    ├── JSON-LD Terminal (syntax-highlighted typewriter on scroll-enter)
    └── Google Maps Embed (sepia/contrast dark filter)
```

---

## ✨ Features

### 🎬 Visual Effects & Interactions

| Effect | Description |
|---|---|
| **Boot Loader** | CSS-only chevron ribbon animation with branded text — no JS dependency |
| **WebGL Gridscan** | Custom GLSL fragment shader rendering an infinite perspective grid with animated scan pulse. Mouse-reactive skew via `IntersectionObserver` (only renders when hero is visible) |
| **3D Particle System** | Canvas-based sphere of 50 particles (25 on mobile) with perspective projection, bounding-sphere physics, and connection lines using squared-distance optimization |
| **Phone Glitch Mask** | Canvas compositing effect — hovering over the hero reveals the phone's internals through a pixel-block reveal pattern with staggered noise and horizontal scan glitch lines |
| **3D Services Tunnel** | CSS `preserve-3d` tunnel with scroll-driven camera movement. Service cards float in z-space with alternating x-spread and rotation. Category text alternates between stroke-only and filled states |
| **Glitch Page Transition** | 10×10 grid overlay with random red/black cell flicker (staggered GSAP animation) between page navigations |
| **Menu Morph Button** | Circle squash-stretch animation with label swap (MENU ↔ CLOSE) |
| **Crosshair Cursor** | Custom desktop cursor with horizontal/vertical lines, center dot, and SVG `feTurbulence` → `feDisplacementMap` glitch effect on interactive element hover |
| **Char-by-char Hero** | Headline text split into individual `<span>` elements, animated sequentially with GSAP stagger and `back.out` easing |
| **Terminal Typewriter** | JSON-LD structured data rendered character-by-character with syntax highlighting (keys = red, strings = green, numbers = cyan). Triggered on scroll entry via `ScrollTrigger` |
| **Interactive Font Footer** | "ACETECH" text where each character tracks mouse proximity and scales/fades based on distance |
| **Scanline Overlay** | Fixed full-screen CRT scanline effect via `repeating-linear-gradient` |

### ⚡ Performance Optimizations

- **GPU-only animations** — exclusively `transform` and `opacity` (no layout/paint thrashing)
- **`force3D: true`** on all GSAP tweens for hardware-accelerated compositing
- **Adaptive particle count** — 50 particles on desktop, 25 on mobile
- **`IntersectionObserver`** gates — WebGL gridscan and 3D tunnel only render when visible
- **Scroll delta gating** — tunnel skips frames when scroll delta < 0.5px
- **Pointer detection** — heavy cursor effects disabled on touch devices via `(pointer: coarse)` media query
- **`loading="lazy"`** on all Facebook iframes and off-screen images
- **`prefers-reduced-motion`** respected — particles stop, tunnel shows static layout
- **Debounced resize** handlers (150ms) to avoid layout thrashing
- **AVIF images** — next-gen compression for all visual assets
- **Single HTTP request** — entire app is one file (no CSS/JS bundle requests)

### 🔍 SEO & Local Business

- **JSON-LD** structured data (`LocalBusiness` schema) in `<head>` and terminal section
- **Open Graph** + Twitter Card meta tags
- **Semantic HTML5** — proper heading hierarchy (`h1` → `h3`), `<main>`, `<header>`, `<footer>`, `<article>`, `<nav>`, `<section>`
- **ARIA attributes** — `role`, `aria-label` on navigation, overlays, and interactive elements
- **Geo-service keywords** — Olongapo City, East Tapinac, Subic Bay, Zambales
- **Canonical URL** and descriptive meta description
- **Google Maps embed** with dark-themed filter

### 🕐 Live Business Features

- **Real-time OPEN/CLOSED status** — computed from Philippine timezone business hours (Mon–Sat schedule with per-day opening times)
- **Live PH clock** — updates every second in footer
- **Status dot indicators** — green blinking (open) / red static (closed) throughout the site

---

## 🚀 Getting Started

No build step. No `npm install`. Just serve it.

```bash
# Clone the repo
git clone https://github.com/ravjansky/AceTech.git
cd AceTech

# Option 1: XAMPP / Apache
# Drop into htdocs/ and visit http://localhost/AceTech

# Option 2: VS Code Live Server
# Right-click index.html → Open with Live Server

# Option 3: Python
python -m http.server 3000

# Option 4: Node
npx serve .
```

---

## 📁 Project Structure

```
AceTech/
├── index.html           # Entire SPA — markup, styles (~1,590 lines), scripts (~1,150 lines)
├── Aero.ttf             # Custom display font
├── acetech-logo.avif    # Logo (navbar + footer)
├── phone-inner.avif     # Phone internals image (hero)
├── phone-outer.avif     # Phone casing overlay (hero canvas compositing)
├── favicon.ico          # Favicon (ICO format)
├── favicon.png          # Favicon (PNG fallback)
├── favicon.avif         # Favicon (AVIF — modern browsers)
├── webclip.png          # iOS home screen icon (256×256)
├── .gitignore
└── README.md
```

> **Design philosophy:** Everything lives in a single HTML file — CSS in `<style>`, JS in `<script>`. No external stylesheets, no separate JS bundles, no build pipeline. The only external dependencies are CDN-loaded: GSAP, ScrollTrigger, Lenis, and JetBrains Mono font.

---

## 🌐 Deployment

The site is deployed on **Cloudflare Pages** with automatic deployments from the `main` branch.

| Environment | URL |
|---|---|
| **Production** | [acetech-eby.pages.dev](https://acetech-eby.pages.dev) |
| **Repository** | [github.com/ravjansky/AceTech](https://github.com/ravjansky/AceTech) |

---

## 📝 Technical Notes

- **Facebook embeds** use `grayscale(1) brightness(0.6)` CSS filters to match the dark theme, transitioning to full color on hover. An overlay `<a>` tag blocks all iframe interaction to prevent lag from Facebook's heavy JS
-  **Google Maps** uses `sepia(0.35) saturate(0.7) brightness(0.6) hue-rotate(-15deg) contrast(1.15)` to create a warm dark-themed map
- **Crosshair cursor** is desktop-only — hidden on touch devices via `@media (pointer: coarse)` and JS detection
- **WebGL gridscan** uses `OES_standard_derivatives` extension for anti-aliased grid lines via `fwidth()`
- **3D tunnel** uses native CSS `perspective` and `transform-style: preserve-3d` (no WebGL/Three.js) — items are positioned along the z-axis and driven purely by scroll position
- **Phone glitch effect** uses a dual-layer canvas approach — the outer phone image is drawn to canvas, then blocks are cleared to reveal the inner image underneath via HTML stacking

---

## 🎨 Design System

```
Colors:
  --deep-black    #0B0B0B     Background
  --red           #E11D2A     Primary accent
  --white         #FFFFFF     Text
  --slate         #708090     Secondary text

Fonts:
  Display         'Aero' (custom .ttf)
  Body            'JetBrains Mono' (Google Fonts CDN)
```

---

## 📞 Business Information

| | |
|---|---|
| **Business** | Acetech Repair and Phones Accessories |
| **Owner** | Ace (Lead Technician) |
| **Specialties** | Micro-Soldering, Logic Board Repair, LCD Resurrection |
| **Address** | 104 Rizal Avenue Extension, East Tapinac, Olongapo City, 2200 Zambales, PH |
| **Phone** | [0968 458 9577](tel:09684589577) |
| **Facebook** | [facebook.com/Acetech07](https://www.facebook.com/Acetech07) |
| **Hours** | Mon–Sat: 10:00 AM – 9:00 PM · Sunday: Closed |
| **Services** | Mobile Device Repair · Board Repair · Laptop & PC · Accessories |

---

## 👤 Credits

**Client:** Ace — Acetech Repair and Phones Accessories  
**Developer:** [ravjansky](https://github.com/ravjansky)

---

<p align="center">
  <sub>Zero frameworks. Just craft. ⚡</sub>
</p>