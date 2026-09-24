# Design System Master File

> **LOGIC:** When building a specific page, first check `design-system/dkrn/pages/[page-name].md`.
> If that file exists, its rules **override** this Master file.
> If not, strictly follow the rules below.

---

**Project:** DKRN Deckungskonzepte Rhein-Neckar
**Category:** Insurance broker (Versicherungsmakler), Privat- und Gewerbekunden
**Generated with:** ui-ux-pro-max `--design-system "insurance broker premium trust" --variance 6 --motion 6 --density 3`
**Design Dials:** Variance 6/10 (Balanced / Modern) | Motion 6/10 (Standard) | Density 3/10 (Spacious)
**Reference implementation:** `index.html`

### Where this file deviates from the generated output

The skill proposed a light "Security blue + protected green" palette with IBM Plex Sans.
Those values are **replaced** by the DKRN brand (logo colours) and the dark premium look
the client chose from a reference video. Kept from the skill: page pattern
"Trust & Authority + Conversion", accessibility rules, spacious density, motion rules,
anti-patterns and the pre-delivery checklist.

---

## Global Rules

### Brand

- Logo: `assets/dkrn-logo.jpg` (original, for light backgrounds).
- On dark backgrounds the mark is rebuilt in HTML: "D" + wine chevron (SVG polygon
  `0,0 28,0 60,50 28,100 0,100 32,50`) + "RN" in Poppins 700; claim
  "DECKUNGSKONZEPTE / RHEIN-NECKAR" in Poppins 300, letter-spacing 0.2em.
- Logo source colours: brown `#3A2D28`, wine `#6E2433`.

### Color Palette (dark, single theme by design)

| Role | Hex | CSS Variable | Contrast on `--bg` |
|------|-----|--------------|--------------------|
| Background | `#0C0908` | `--bg` | – |
| Background 2 | `#14100E` | `--bg-2` | – |
| Surface / Card | `#1A1412` | `--surface` | – |
| Foreground | `#F3ECE7` | `--ink` | 17.0:1 |
| Muted Foreground | `#A89C95` | `--ink-soft` | 7.4:1 |
| Faint Foreground | `#8A7F79` | `--ink-faint` | 5.1:1 |
| Primary / CTA fill | `#7A2436` | `--wine` | text `--ink` on it 8.4:1 |
| Primary hover / glow | `#C04D63` | `--wine-bright` | decorative only |
| Wine as text | `#D0677D` | `--wine-text` | 5.6:1 |
| Accent (headline 2nd line, icons) | `#D2B287` | `--champagne` | 9.9:1 |
| Accent muted (eyebrows) | `#9C8262` | `--champagne-soft` | 5.5:1 |
| Border | `rgba(243,236,231,.12)` | `--line` | – |
| Border strong | `rgba(243,236,231,.28)` | `--line-strong` | – |
| Footer background | `#7A2436` | `--wine` | text `#FBEFF1` 8.8:1 |

**Color Notes:** Warm black + wine from the logo's K chevron + champagne instead of gold.
Wine is the only CTA colour. Never put `--wine` or `--wine-bright` on dark as body text.

### Typography

- **Headings:** Newsreader 300 (serif), two-tone: line 1 `--ink`, line 2 (`<em>`) `--champagne`
- **Body:** Manrope 400/500/600
- **Brand / UI / eyebrows:** Poppins 300–700 (matches the logo)
- **Scale:** hero `clamp(42px, 6.4vw, 86px)`, section `clamp(34px, 5.2vw, 68px)`, body 16px / 1.6, lead 17px
- **Eyebrow:** Poppins 500, 12px, uppercase, letter-spacing 0.22em
- **Google Fonts:** `https://fonts.googleapis.com/css2?family=Newsreader:ital,opsz,wght@0,6..72,300;0,6..72,400;1,6..72,300&family=Poppins:wght@300;400;600;700&family=Manrope:wght@400;500;600&display=swap`

### Spacing Variables

*Density: 3/10 — Spacious*

| Token | Value | Usage |
|-------|-------|-------|
| `--gutter` | `clamp(16px, 4vw, 56px)` | Page side padding |
| section padding | `clamp(80px, 11vw, 150px)` | Vertical section rhythm |
| card padding | `32px` | Duo cards |
| grid gap | `20–32px` | Cards, features |

### Radius & Shadow

| Element | Radius | Shadow |
|---------|--------|--------|
| Buttons | `999px` (pill) | primary: `0 10px 30px -10px rgba(192,77,99,.6)` |
| Duo cards | `24px` | none, border `--line` |
| Glow card | `28px` | none, radial wine/champagne gradients |
| 3D tiles | `18px` | `0 30px 60px -20px rgba(0,0,0,.9)` |

---

## Component Specs

### Buttons

- `.btn-primary`: wine fill, `--ink` text, hover `--wine-bright`, lift `translateY(-2px)`
- `.btn-ghost`: transparent, `--line-strong` border, hover champagne border and text
- `.btn-light`: `--ink` fill, `--bg` text (header CTA, glow card)
- Min height 44px (header) / 48px (content), Poppins 600 14px, transition 200ms

### Cards

- Duo cards (Privat / Gewerbe): surface gradient, `--line` border, hover border `--line-strong` + lift 4px,
  eyebrow + serif title + text + chips + illustration at the bottom
- Glow card: statement + one CTA; light spot follows the pointer (`--mx`, `--my`)

### Trust row

- 4 items: Unabhängig · Registriert (§ 34d GewO) · Abgesichert (VSH) · Persönlich
- Only factual claims. No invented numbers, ratings or insurer logos.

### FAQ

- Native `<details>/<summary>`, champagne plus/minus, 44px+ tap height

---

## Style Guidelines

**Style:** Dark premium + Accessible & Ethical

**Key Effects:** Two-tone serif headlines, floating 3D tiles in hero, region marquee,
glowing line icons drawn on scroll, streak lines behind final CTA, wine footer with giant wordmark.
Clear focus rings (3px champagne), skip link, 44x44px touch targets.

### Page Pattern

**Pattern Name:** Trust & Authority + Conversion

- **Section Order:** Hero (claim + CTA) > Region marquee > Statement + trust row > Glow card >
  Privat / Gewerbe > Leistungen > Ablauf (4 steps) > FAQ > Final CTA > Footer
- **CTA Placement:** "Termin vereinbaren" in nav + hero primary "Kostenlose Analyse anfragen" + final CTA
- **Marquee:** pauses on hover, focus, via pause button (`aria-pressed`), when offscreen, and is static under reduced motion

---

## Motion

- Entrance: headline lines slide up (1100ms, `cubic-bezier(.2,.7,.1,1)`), copy fades up with 380–520ms delay
- Scroll reveal: opacity + translateY(28px), 1000ms; only for elements starting below the fold
- Ambient: tiles float 6s, rings pulse 5s, streaks 5–14s; all paused when their section is offscreen
- Hover: 150–300ms
- `prefers-reduced-motion: reduce` disables all animation and shows the final state

---

## Anti-Patterns (Do NOT Use)

- ❌ Confusing pricing
- ❌ No trust signals
- ❌ AI purple/pink gradients
- ❌ Fake testimonials, invented statistics or insurer logos without a real partnership

### Additional Forbidden Patterns

- ❌ **Emojis as icons** — Use SVG icons
- ❌ **Missing cursor:pointer** — All clickable elements must have cursor:pointer
- ❌ **Layout-shifting hovers** — Avoid scale transforms that shift layout
- ❌ **Low contrast text** — Maintain 4.5:1 minimum contrast ratio
- ❌ **Instant state changes** — Always use transitions (150-300ms)
- ❌ **Invisible focus states** — Focus states must be visible for a11y

---

## Pre-Delivery Checklist

Before delivering any UI code, verify:

- [ ] No emojis used as icons (use SVG instead)
- [ ] All icons in the same line style (1.6 stroke, round caps)
- [ ] `cursor-pointer` on all clickable elements
- [ ] Hover states with smooth transitions (150-300ms)
- [ ] Text contrast 4.5:1 minimum (see table above)
- [ ] Focus states visible for keyboard navigation, skip link present
- [ ] `prefers-reduced-motion` respected
- [ ] Responsive: 375px, 768px, 1024px, 1440px
- [ ] No content hidden behind fixed navbars (`scroll-margin-top` on anchors)
- [ ] No horizontal scroll on mobile
- [ ] Legal: Impressum, Datenschutz, Erstinformation, § 34d registration number filled in
