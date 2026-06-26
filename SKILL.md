---
name: design-effects-skill
description: >-
  Visual effects and animation patterns for UI and branding contexts. Use when
  choosing or implementing animated backgrounds, text effects, morphism styles,
  micro-interactions, motion patterns, liquid/glass FX, shader gradients, depth
  systems, border effects, or 3D elements. Activate on: "add animation",
  "make it more dynamic", "animated background", "text effect", "visual effect",
  "glassmorphism", "neumorphism", "claymorphism", "brutalism", "bento grid",
  "shader", "3D hero", "micro-interaction", "hover effect", "loading state",
  "gradient border", "/design-effects-skill".
trigger_keywords:
  - animation
  - animated background
  - text effect
  - visual effect
  - glassmorphism
  - neumorphism
  - claymorphism
  - brutalism
  - bento grid
  - liquid glass
  - shader gradient
  - motion
  - 3D UI
  - particle background
  - scroll animation
  - micro-interaction
  - hover effect
  - loading skeleton
  - gradient border
  - glow effect
  - variable font
  - /design-effects-skill
author: bilioveloso
version: "2.0"
---

# Design Effects Skill

## Purpose
This skill teaches an agent to make better visual effect decisions — from choosing a morphism style to picking the right scroll animation to knowing when NOT to add effects at all. For any visual output requiring motion, depth, texture, or atmosphere, the agent should:

1. Identify the context, brand tier, and performance budget.
2. Use the Decision Guide to match to an effect category.
3. Pick the named effect that fits.
4. Apply the minimal code snippet as a starting point.
5. Cross-reference color-combo-skill for palette pairing.

## Core Rules
- **Never add effects for the sake of effects.** Every animation or visual style must serve a purpose — atmosphere, feedback, or focus.
- **Performance first.** Heavy effects (3D, shaders, particles) are only justified on hero sections or dedicated visual moments, never on every element.
- **One hero effect per page.** If a page has a ShaderGradient hero, it doesn't also need particle backgrounds and liquid glass cards.
- **Mobile check.** Shader and 3D effects can be expensive on mobile. Always provide a static fallback.
- **Morphism needs a background.** Glass, clay, and neuo effects only work when there is something behind the surface — a flat background kills all of them.
- **Neumorphism and accessibility are enemies.** The soft shadow technique almost always fails WCAG contrast. Never use neumorphism for text-heavy or interactive UI without a contrast audit.
- **Color bridge.** When choosing colors for any effect, reference [color-combo-skill](https://github.com/bilioveloso/color-combo-skill) palettes rather than picking arbitrary hex values.

---

## Decision Guide

### By goal

| Goal | Effect / Category |
|---|---|
| Immersive, breathing hero background | Animated Backgrounds → ShaderGradient or Aurora |
| Subtle, textured background | Animated Backgrounds → DotGrid, Grid, or Noise |
| Interactive particle atmosphere | Animated Backgrounds → Particles or Orbs |
| High-energy cinematic moment | Animated Backgrounds → Hyperspeed |
| Hero text that demands attention | Text Animations → SplitText or BlurText |
| Counting numbers / stats | Text Animations → CountUp |
| Multiple value props in one headline | Text Animations → RotatingText |
| Text as visual texture or decoration | Typography Effects → Oversized Display or Outlined Text |
| Scroll-triggered content reveals | Motion & Scroll → ScrollReveal or FadeContent |
| Staggered list or grid entrance | Motion & Scroll → Stagger |
| Scroll-linked depth on hero | Motion & Scroll → Parallax |
| Page-to-page transitions | Motion & Scroll → Page Transitions |
| Hover micro-interactions on UI | UI Components → Magnet, TiltCard, SpotlightCard |
| Button feedback / press states | Micro-interactions → Button States |
| Loading / async content | Micro-interactions → Skeleton or Spinner |
| Success / error feedback | Micro-interactions → State Animations |
| Premium frosted overlay or card | Design Morphisms → Glassmorphism |
| Soft, tactile, extruded UI surface | Design Morphisms → Neumorphism |
| Inflated, cartoon-soft card | Design Morphisms → Claymorphism |
| Raw, high-contrast, structural | Design Morphisms → Brutalism |
| SaaS feature section layout | Layout Patterns → Bento Grid |
| Scrolling ticker or marquee | Layout Patterns → Infinite Scroll / Marquee |
| Premium brand logo animation | Liquid & Glass FX → liquid-logo |
| Apple-style distortion overlay | Liquid & Glass FX → liquid-glass-js |
| Glowing or gradient border | Border & Glow Effects → Gradient Border or Glow |
| Animated neon outline | Border & Glow Effects → Animated Glow |
| 3D product viewer or abstract hero | 3D in UI → react-three-fiber |

### By brand tier

| Brand tier | Appropriate effects | Never use |
|---|---|---|
| **Enterprise / B2B** | DotGrid, FadeContent, subtle SpotlightCard, Skeleton loaders | Claymorphism, Brutalism, Hyperspeed, Ballpit |
| **Premium / Luxury** | ShaderGradient, Glassmorphism, liquid-logo, BlurText, GradientText | Claymorphism, Neumorphism, Pixel effects |
| **Consumer / Lifestyle** | Aurora, Waves, Claymorphism, TiltCard, Marquee, CountUp | Heavy 3D, Hyperspeed |
| **Gaming / Esports** | Hyperspeed, Particles, GlitchText, Glow borders, Ballpit | Glassmorphism (unless dark tinted), Neumorphism |
| **Wellness / Healthcare** | Waves, Aurora, FadeContent, soft Glassmorphism | Glitch, Hyperspeed, Acid effects |
| **Creative / Portfolio** | Any — but one hero effect only, everything else restrained | Stacking 3+ heavy effects |
| **Developer Tool / SaaS** | DotGrid, ShaderGradient, ScrollReveal, Skeleton, Brutalism accents | Claymorphism, Liquid effects |

---

## Design Morphisms

Morphism styles define the visual language of surfaces and cards. They are not animations — they are material languages. Choose one per project and apply it consistently.

> **Agent rule:** Never mix morphism styles in the same UI. Glassmorphism cards next to neumorphic buttons is a failure state. Pick one material language and commit.

### Glassmorphism
- **What it is:** Frosted glass effect using `backdrop-filter: blur()`. The element appears to float above the background with a translucent, blurred surface.
- **Best for:** Overlays on photo/gradient/video backgrounds, premium UI, modals, navigation bars on hero sections, Apple-adjacent products.
- **Avoid when:** The background is flat or solid — glass with nothing behind it is invisible. Also avoid in dense data UIs where subtle surfaces create noise.
- **Color pairing:** Works on any rich background — use Luxury, Soft Gradients, or Otherworldly palettes behind the glass.

```css
/* Standard glass card */
.glass-card {
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(20px) saturate(180%);
  -webkit-backdrop-filter: blur(20px) saturate(180%);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 16px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
}

/* Dark tinted glass (gaming / gothic) */
.glass-card--dark {
  background: rgba(0, 0, 0, 0.35);
  backdrop-filter: blur(24px) saturate(160%);
  -webkit-backdrop-filter: blur(24px) saturate(160%);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 12px;
}

/* Colored tinted glass (brand accent) */
.glass-card--tinted {
  background: rgba(43, 238, 52, 0.08); /* Silver Pulse accent — Otherworldly */
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(43, 238, 52, 0.18);
  border-radius: 14px;
}
```

**Browser note:** `backdrop-filter` requires `-webkit-` prefix for Safari. It is unsupported in Firefox by default (user must enable `layout.css.backdrop-filter.enabled`). Always test or provide a solid-background fallback.

```css
/* Fallback for Firefox */
@supports not (backdrop-filter: blur(1px)) {
  .glass-card {
    background: rgba(20, 20, 30, 0.85);
  }
}
```

### Neumorphism
- **What it is:** Soft UI — elements appear extruded from or pressed into the background using dual layered shadows (light from top-left, dark from bottom-right). The element and background share the same color.
- **Best for:** Premium calm apps (meditation, wellness, audio players), tactile dashboard widgets, decorative UI moments.
- **Avoid when:** Text contrast is required — neumorphism almost always fails WCAG 4.5:1 on interactive elements. Never use on buttons that need to be clearly clickable, form inputs, or any accessibility-critical context.
- **Color pairing:** Requires a mid-tone base — works best with Minimalist (Warm Mono, Bone & Carbon) or soft Healthcare palettes. Never on pure black or white.

```css
/* Extruded (raised) neumorphic surface */
.neuo-raised {
  background: #E8E0D8; /* Warm Mono secondary — Minimalist */
  border-radius: 16px;
  box-shadow:
    8px 8px 16px rgba(0, 0, 0, 0.15),
    -8px -8px 16px rgba(255, 255, 255, 0.7);
}

/* Inset (pressed) neumorphic surface */
.neuo-inset {
  background: #E8E0D8;
  border-radius: 16px;
  box-shadow:
    inset 6px 6px 12px rgba(0, 0, 0, 0.15),
    inset -6px -6px 12px rgba(255, 255, 255, 0.7);
}
```

**Accessibility warning:** Always run a contrast check. If the element contains text or is interactive, neumorphism is likely not appropriate without a separate high-contrast text treatment.

### Claymorphism
- **What it is:** 3D inflated, rounded, soft surfaces that look like clay or inflatable objects. Achieved with large border-radius, thick colored outer glow, inner highlight, and subtle 3D shadow.
- **Best for:** Consumer mobile apps, children's products, playful SaaS onboarding, lifestyle brands, Dribbble-adjacent portfolios.
- **Avoid when:** Enterprise, healthcare (clinical), or any context requiring seriousness and trust. Clay signals playful, not professional.
- **Color pairing:** Works best with bright, saturated pastels — use Luxury Facade, Warm Tropical/Resort, or custom pastels. Always use a light or white background behind clay elements.

```css
.clay-card {
  background: #FFD3B6; /* Peach Champagne — Soft Gradients */
  border-radius: 28px;
  box-shadow:
    0 8px 0px rgba(0, 0, 0, 0.15),          /* ground shadow */
    0 16px 40px rgba(0, 0, 0, 0.12),         /* depth shadow */
    inset 0 -4px 8px rgba(0, 0, 0, 0.08),    /* bottom inner shadow */
    inset 0 4px 8px rgba(255, 255, 255, 0.6); /* top inner highlight */
  border: 3px solid rgba(255, 255, 255, 0.6);
}

/* Clay button */
.clay-button {
  background: #B8C0FF; /* Dreamy Periwinkle */
  border-radius: 50px;
  padding: 14px 32px;
  box-shadow:
    0 6px 0px #8890D8,
    0 10px 24px rgba(0, 0, 0, 0.15),
    inset 0 3px 6px rgba(255, 255, 255, 0.5);
  border: 2px solid rgba(255, 255, 255, 0.5);
  font-weight: 700;
}
```

### Brutalism
- **What it is:** Raw, exposed, anti-polish design. Hard borders, flat colors, visible structure, high contrast, intentional roughness. Rejects decoration in favor of directness.
- **Best for:** Developer tools, independent SaaS, editorial publications, creative agencies, alt-culture brands, projects where authenticity > refinement.
- **Avoid when:** The audience is conservative (enterprise, finance, healthcare), or the brand needs to convey safety and trust.
- **Color pairing:** Acid Contemporary, Refined Defaults (pushed to extremes), or literal black/white. Brutalism earns the right to use #000000.

```css
/* Brutalist card */
.brutal-card {
  background: #F5E800; /* Ink Volt secondary — Acid Contemporary */
  border: 3px solid #0A0A0A;
  border-radius: 0;
  box-shadow: 6px 6px 0px #0A0A0A;
  padding: 24px;
}

/* Brutalist button */
.brutal-button {
  background: #0A0A0A;
  color: #F5E800;
  border: 3px solid #0A0A0A;
  border-radius: 0;
  box-shadow: 4px 4px 0px #F5E800;
  font-weight: 900;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  padding: 12px 28px;
  cursor: pointer;
  transition: box-shadow 0.1s, transform 0.1s;
}

.brutal-button:hover {
  box-shadow: 2px 2px 0px #F5E800;
  transform: translate(2px, 2px);
}
```

---

## Micro-interactions

The smallest unit of design feedback. Micro-interactions make a UI feel alive and responsive. They are not decorative — they communicate state, confirm actions, and reduce uncertainty.

> **Agent rule:** Every interactive element needs a hover state, active/press state, and focus state. Missing any of these is an incomplete implementation.

### Button States
All buttons need all four states. Missing states make the UI feel broken.

```css
.button {
  background: #2A7AE8; /* Steel Authority accent — Corporate */
  color: #ffffff;
  border: none;
  border-radius: 8px;
  padding: 12px 24px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s ease, transform 0.1s ease, box-shadow 0.15s ease;
}

/* Hover — lighten or lift */
.button:hover {
  background: #4A90F0;
  box-shadow: 0 4px 16px rgba(42, 122, 232, 0.35);
  transform: translateY(-1px);
}

/* Active / press — push down */
.button:active {
  background: #1A5AB8;
  transform: translateY(1px);
  box-shadow: none;
}

/* Focus — keyboard accessibility */
.button:focus-visible {
  outline: 3px solid #2A7AE8;
  outline-offset: 3px;
}

/* Disabled */
.button:disabled {
  background: #A8B8CC;
  cursor: not-allowed;
  transform: none;
  box-shadow: none;
}
```

### Loading States — Skeleton vs. Spinner
Choose based on what you know about the content shape.

| Use | When |
|---|---|
| **Skeleton screen** | You know the layout of the content being loaded (cards, lists, profiles) |
| **Spinner** | Unknown duration, unknown content shape, or a small inline action |
| **Progress bar** | File uploads, multi-step processes, known completion percentage |
| **Shimmer skeleton** | Preferred over static skeleton — communicates active loading |

```css
/* Shimmer skeleton */
.skeleton {
  background: linear-gradient(
    90deg,
    #E8E0D8 25%,
    #F5F0EB 50%,
    #E8E0D8 75%
  );
  background-size: 200% 100%;
  animation: shimmer 1.4s infinite;
  border-radius: 6px;
}

@keyframes shimmer {
  0% { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}

/* Skeleton line examples */
.skeleton-title { width: 60%; height: 20px; margin-bottom: 12px; }
.skeleton-body  { width: 100%; height: 14px; margin-bottom: 8px; }
.skeleton-avatar { width: 48px; height: 48px; border-radius: 50%; }
```

### Success / Error State Animations
State changes need motion to be noticed. Static color swaps are often missed.

```css
/* Success — green pulse */
@keyframes success-pulse {
  0%   { box-shadow: 0 0 0 0 rgba(26, 138, 64, 0.4); }
  70%  { box-shadow: 0 0 0 10px rgba(26, 138, 64, 0); }
  100% { box-shadow: 0 0 0 0 rgba(26, 138, 64, 0); }
}
.state-success {
  border-color: #1A8A40; /* Vital Green accent — Healthcare */
  animation: success-pulse 0.6s ease-out;
}

/* Error — red shake */
@keyframes error-shake {
  0%, 100% { transform: translateX(0); }
  20%      { transform: translateX(-6px); }
  40%      { transform: translateX(6px); }
  60%      { transform: translateX(-4px); }
  80%      { transform: translateX(4px); }
}
.state-error {
  border-color: #D7202D;
  animation: error-shake 0.4s ease-out;
}
```

### Hover Reveal Patterns
Common hover interactions that add depth without heavy libraries.

```css
/* Underline grow */
.link-underline {
  position: relative;
  text-decoration: none;
}
.link-underline::after {
  content: '';
  position: absolute;
  bottom: -2px; left: 0;
  width: 0; height: 2px;
  background: currentColor;
  transition: width 0.25s ease;
}
.link-underline:hover::after { width: 100%; }

/* Card lift */
.card-lift {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.card-lift:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 32px rgba(0, 0, 0, 0.15);
}

/* Image zoom on hover */
.img-zoom { overflow: hidden; }
.img-zoom img {
  transition: transform 0.4s ease;
}
.img-zoom:hover img { transform: scale(1.06); }
```

---

## Typography Effects

Type is a design element, not just content delivery. These effects use typography itself as the visual layer.

> **Agent rule:** Typography effects only work when the typeface is strong. A weak font with a gradient fill is just a weak font with a gradient fill. Confirm the typeface is appropriate before adding effects.

### Variable Font Animations
- **What it is:** Variable fonts expose axes (weight, width, slant) that can be animated with CSS transitions. The result is type that morphs smoothly.
- **Best for:** Interactive headlines, hover-reactive type, scroll-driven weight shifts.
- **Requires:** A variable font with the relevant axis (check with `font-variation-settings`).

```css
.variable-headline {
  font-family: 'Inter Variable', sans-serif;
  font-variation-settings: 'wght' 300;
  transition: font-variation-settings 0.3s ease;
}

.variable-headline:hover {
  font-variation-settings: 'wght' 800;
}

/* Scroll-driven weight — pair with JS scroll listener */
/* wght value maps from 300 (top of page) to 900 (bottom) */
```

### Outlined / Stroke Text
- **What it is:** Text with no fill, only a visible stroke outline. Creates a ghost-type effect that feels structural and bold without visual weight.
- **Best for:** Background decorative type layers, oversized section labels, brutalist and editorial layouts.
- **Avoid when:** Readability is the primary goal — stroke text is decoration, not content.

```css
/* CSS stroke text */
.text-outline {
  -webkit-text-stroke: 2px #0A0A0A;
  color: transparent;
  font-size: clamp(4rem, 10vw, 10rem);
  font-weight: 900;
  line-height: 1;
  letter-spacing: -0.02em;
  user-select: none;
}

/* Stroke with hover fill */
.text-outline-hover {
  -webkit-text-stroke: 2px #D4AF37; /* Golden Obsession accent */
  color: transparent;
  transition: color 0.3s ease;
}
.text-outline-hover:hover {
  color: #D4AF37;
}
```

### Oversized Display Type as Texture
- **What it is:** Typography scaled so large it becomes a background element — text as pattern, not message.
- **Best for:** Section backgrounds, hero decorative layers, editorial poster layouts.
- **Technique:** Low opacity, large scale, `pointer-events: none`, positioned absolutely behind content.

```css
.display-texture {
  position: absolute;
  font-size: clamp(8rem, 20vw, 20rem);
  font-weight: 900;
  opacity: 0.04;
  white-space: nowrap;
  pointer-events: none;
  user-select: none;
  letter-spacing: -0.05em;
  line-height: 1;
  z-index: 0;
}
```

### Gradient Text Fill
```css
/* Animated flowing gradient text */
.gradient-text {
  background: linear-gradient(
    90deg,
    #B8C0FF, #E7D8FF, #D6C6F7, #B8C0FF /* Dreamy Periwinkle — Soft Gradients */
  );
  background-size: 200% auto;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient-flow 3s linear infinite;
}

@keyframes gradient-flow {
  0%   { background-position: 0% center; }
  100% { background-position: 200% center; }
}
```

### Kinetic Typography Rules
When type moves as a primary visual element (not just an entrance animation):
- Speed must reflect brand energy: slow (0.8–1.2s) = premium/editorial; fast (0.2–0.4s) = tech/gaming
- Never move more than one text element simultaneously in the viewport
- Kinetic type needs breathing room — generous whitespace, minimal surrounding elements
- Always loop cleanly or stop at a natural resting state

---

## Depth & Shadow System

Shadow is not decoration — it is depth. A consistent shadow system makes a UI feel physically coherent rather than randomly layered.

> **Agent rule:** Pick one shadow style per project (flat, elevated, or dramatic) and apply it at consistent scales. Never mix flat design with heavy drop shadows on adjacent elements.

### Elevation Scale
Five levels cover all use cases. Map them to z-index levels too.

```css
:root {
  /* Level 0 — flat, no elevation */
  --shadow-0: none;

  /* Level 1 — subtle, card resting */
  --shadow-1: 0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.06);

  /* Level 2 — card hover, dropdown */
  --shadow-2: 0 4px 12px rgba(0,0,0,0.10), 0 2px 4px rgba(0,0,0,0.06);

  /* Level 3 — modal, overlay, popover */
  --shadow-3: 0 8px 32px rgba(0,0,0,0.14), 0 4px 8px rgba(0,0,0,0.08);

  /* Level 4 — floating action, full-screen modal */
  --shadow-4: 0 20px 60px rgba(0,0,0,0.20), 0 8px 20px rgba(0,0,0,0.10);
}
```

### Colored Shadows
Colored shadows (matching the element color) feel more premium than grey shadows. Use on cards, buttons, and hero elements.

```css
/* Button with colored glow shadow */
.button-glow {
  background: #2A7AE8;
  box-shadow: 0 8px 24px rgba(42, 122, 232, 0.4);
}

/* Accent card with tinted shadow */
.card-tinted-shadow {
  background: #1A0A1E; /* Velvet Crypt — Gothic */
  box-shadow: 0 12px 40px rgba(200, 160, 224, 0.2); /* accent color tinted */
}
```

### box-shadow vs. filter: drop-shadow()

| Use | When |
|---|---|
| `box-shadow` | Rectangular elements, cards, buttons — follows the border-box |
| `filter: drop-shadow()` | SVGs, PNGs with transparency, irregular shapes — follows the pixel alpha |
| `text-shadow` | Type only, lightweight, no blur radius above 4px |

```css
/* drop-shadow on an SVG icon (follows the icon shape, not its bounding box) */
.icon-shadow {
  filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.3));
}
```

---

## Border & Glow Effects

Borders and outlines as active design elements — not just structural dividers.

> **Agent rule:** Gradient borders and glow effects are accent moments. Never apply to every card or element — reserve for 1–2 hero elements per section.

### Gradient Border
CSS doesn't support `border-image` with `border-radius` directly. Use the pseudo-element technique.

```css
/* Gradient border with border-radius */
.gradient-border {
  position: relative;
  background: #0A0C10; /* Midnight Frag primary — Gaming */
  border-radius: 12px;
  padding: 1px; /* controls border thickness */
}

.gradient-border::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1px;
  background: linear-gradient(135deg, #00E5FF, #006080, #3C1A47);
  -webkit-mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
}

.gradient-border__inner {
  background: #0A0C10;
  border-radius: 11px;
  padding: 24px;
}
```

### Animated Glow / Neon Border
```css
/* Pulsing neon glow — Gaming / Esports */
@keyframes glow-pulse {
  0%, 100% { box-shadow: 0 0 8px #00E5FF, 0 0 20px rgba(0, 229, 255, 0.4); }
  50%       { box-shadow: 0 0 16px #00E5FF, 0 0 40px rgba(0, 229, 255, 0.6); }
}

.neon-card {
  border: 1px solid #00E5FF;
  border-radius: 8px;
  animation: glow-pulse 2s ease-in-out infinite;
}

/* Rotating gradient border animation */
@keyframes border-spin {
  0%   { --border-angle: 0deg; }
  100% { --border-angle: 360deg; }
}

@property --border-angle {
  syntax: '<angle>';
  initial-value: 0deg;
  inherits: false;
}

.spinning-border {
  border: 2px solid transparent;
  border-radius: 12px;
  background:
    linear-gradient(#0A0C10, #0A0C10) padding-box,
    conic-gradient(from var(--border-angle), #00E5FF, #3C1A47, #B6FF00, #00E5FF) border-box;
  animation: border-spin 3s linear infinite;
}
```

### Subtle Glow on Hover (Premium)
```css
.card-hover-glow {
  transition: box-shadow 0.3s ease;
}

.card-hover-glow:hover {
  box-shadow:
    0 0 0 1px rgba(212, 175, 55, 0.3),  /* Golden Obsession accent */
    0 8px 32px rgba(212, 175, 55, 0.15);
}
```

---

## Motion & Scroll

Scroll-triggered animations and transitions. These guide attention rather than demand it.

> **Agent rule:** Scroll animations must use ease-out curves and short durations (200–400ms). Never block content visibility — always animate from visible-enough to fully visible, never from invisible.

### ScrollReveal (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/animations/scroll-reveal) — MIT
- **What it is:** Elements fade and slide into view as they enter the viewport.
- **Best for:** Content sections, feature grids, testimonials.
- **Install:** `npx shadcn@latest add @react-bits/ScrollReveal-TS-TW`

### FadeContent (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/animations/fade-content) — MIT
- **What it is:** Simple opacity fade-in. Minimal and universal.
- **Best for:** Editorial content, long-form pages, documentation.
- **Install:** `npx shadcn@latest add @react-bits/FadeContent-TS-TW`

### Stagger Animation
Animate a list or grid where each item enters with a delay offset. Creates a cascade effect.

```tsx
// Stagger with CSS custom property delay
{items.map((item, i) => (
  <div
    key={item.id}
    className="stagger-item"
    style={{ '--delay': `${i * 80}ms` } as React.CSSProperties}
  >
    {item.content}
  </div>
))}
```

```css
.stagger-item {
  opacity: 0;
  transform: translateY(16px);
  animation: stagger-in 0.4s ease-out var(--delay, 0ms) forwards;
}

@keyframes stagger-in {
  to { opacity: 1; transform: translateY(0); }
}
```

### Parallax Scroll
Background moves at a different speed to foreground, creating depth.

```css
/* CSS-only parallax (limited but zero JS) */
.parallax-section {
  background-attachment: fixed;
  background-position: center;
  background-size: cover;
}
```

```tsx
// JS parallax with scroll listener
useEffect(() => {
  const handleScroll = () => {
    const y = window.scrollY
    if (bgRef.current) {
      bgRef.current.style.transform = `translateY(${y * 0.4}px)`
    }
  }
  window.addEventListener('scroll', handleScroll, { passive: true })
  return () => window.removeEventListener('scroll', handleScroll)
}, [])
```

### Page Transitions
Route-level transitions in React. Use Framer Motion's `AnimatePresence` for the cleanest implementation.

```tsx
import { AnimatePresence, motion } from 'framer-motion'
// install: npm i framer-motion

// Wrap router outlet with AnimatePresence
<AnimatePresence mode="wait">
  <motion.div
    key={location.pathname}
    initial={{ opacity: 0, y: 8 }}
    animate={{ opacity: 1, y: 0 }}
    exit={{ opacity: 0, y: -8 }}
    transition={{ duration: 0.2, ease: 'easeOut' }}
  >
    {children}
  </motion.div>
</AnimatePresence>
```

### GlitchText (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/text-animations/glitch) — MIT
- **What it is:** Glitch/distortion effect on text. Cyberpunk aesthetic.
- **Best for:** Gaming, esports, hacker aesthetic.
- **Avoid when:** Professional, wellness, or corporate contexts.
- **Color pairing:** Otherworldly, Acid Contemporary, Gaming/Esports palettes.
- **Install:** `npx shadcn@latest add @react-bits/GlitchText-TS-TW`

---

## Animated Backgrounds

Use for hero sections, full-page backgrounds, and section transitions. Choose based on performance budget and brand mood.

> **Agent rule:** One animated background per page. Do not stack two animated backgrounds.

### ShaderGradient
- **Source:** [@shadergradient/react](https://github.com/ruucm/shadergradient) — MIT
- **What it is:** 3D animated mesh gradient via WebGL/Three.js.
- **Best for:** AI/tech SaaS hero sections, premium landing pages.
- **Avoid when:** Performance is constrained or users are on low-end mobile.
- **Install:** `npm i @shadergradient/react @react-three/fiber three three-stdlib camera-controls`

```tsx
import { ShaderGradientCanvas, ShaderGradient } from '@shadergradient/react'

export function HeroBackground() {
  return (
    <ShaderGradientCanvas style={{ position: 'absolute', inset: 0 }} pixelDensity={1.5} fov={45}>
      <ShaderGradient
        type="waterPlane" animate="on"
        uSpeed={0.3} uStrength={3} uDensity={1.2}
        color1="#B8C0FF" color2="#E7D8FF" color3="#1A0A1E"
        lightType="3d" brightness={1.2} grain="on"
      />
    </ShaderGradientCanvas>
  )
}
```

**Mobile fallback:**
```css
.hero-bg-fallback { background: linear-gradient(135deg, #B8C0FF 0%, #E7D8FF 100%); }
```

### ShaderGradient Palette Recipes

| Palette (color-combo-skill) | color1 | color2 | color3 | Mood |
|---|---|---|---|---|
| Dreamy Periwinkle | `#B8C0FF` | `#E7D8FF` | `#2D4275` | Soft, digital-premium |
| Golden Obsession | `#D4AF37` | `#1C1A17` | `#B87333` | Opulent, dark luxury |
| Neon Abyss | `#3C1A47` | `#B6FF00` | `#1A0828` | Electric, surreal |
| Midnight Frag | `#00E5FF` | `#0A0C10` | `#1A1E28` | Gaming, high-focus |
| Clinical Clarity | `#D0E8F0` | `#F7FAFB` | `#0A7A8A` | Clean, medical |
| Eucalyptus Glow | `#A7C4A0` | `#F4EFE6` | `#4E6B45` | Organic, wellness |

### Aurora (ReactBits)
- **What it is:** Soft animated aurora gradient. Lightweight CSS/canvas.
- **Best for:** Wellness, premium SaaS, calm editorial.
- **Install:** `npx shadcn@latest add @react-bits/Aurora-TS-TW`

### Particles / Orbs (ReactBits)
- **What it is:** Floating particles or glowing orbs.
- **Best for:** Tech, AI, dark UI hero sections.
- **Install:** `npx shadcn@latest add @react-bits/Particles-TS-TW`

### Hyperspeed (ReactBits)
- **What it is:** Star-warp tunnel speed effect.
- **Best for:** Gaming, esports, launch pages.
- **Avoid when:** Sustained readability is needed — this is a moment, not a surface.
- **Install:** `npx shadcn@latest add @react-bits/Hyperspeed-TS-TW`

### Ballpit (ReactBits)
- **What it is:** Physics-based 3D bouncing balls.
- **Best for:** Playful SaaS, gaming, youthful consumer products.
- **Install:** `npx shadcn@latest add @react-bits/Ballpit-TS-TW`

### Dot Matrix / Grid (ReactBits)
- **What it is:** Subtle animated dot or grid pattern.
- **Best for:** SaaS, developer tools, corporate digital.
- **Install:** `npx shadcn@latest add @react-bits/DotGrid-TS-TW`

### Waves (ReactBits)
- **What it is:** Animated SVG/canvas wave pattern.
- **Best for:** Wellness, fintech, clean section dividers.
- **Install:** `npx shadcn@latest add @react-bits/Waves-TS-TW`

---

## Text Animations

For headlines, hero text, and key callouts only. Never on body copy.

> **Agent rule:** One text animation per view. Two animated text elements in the same viewport is one too many.

### BlurText (ReactBits)
- **What it is:** Text unblurs into focus word by word.
- **Best for:** Hero headlines, premium reveals.
- **Install:** `npx shadcn@latest add @react-bits/BlurText-TS-TW`

```tsx
<BlurText text="Design that speaks." delay={150} animateBy="words" direction="top" className="text-5xl font-bold" />
```

### SplitText (ReactBits)
- **What it is:** Characters/words animate in with spring physics.
- **Best for:** Bold editorial headlines, brand moments.
- **Install:** `npx shadcn@latest add @react-bits/SplitText-TS-TW`

### ShinyText (ReactBits)
- **What it is:** Animated shine sweep. Lightweight CSS.
- **Best for:** Badges, "New" labels, premium callouts.
- **Install:** `npx shadcn@latest add @react-bits/ShinyText-TS-TW`

### GradientText (ReactBits)
- **What it is:** Animated gradient fill on text.
- **Best for:** AI headlines, tech SaaS hero text.
- **Color pairing:** Otherworldly or Soft Gradients palettes.
- **Install:** `npx shadcn@latest add @react-bits/GradientText-TS-TW`

### CountUp (ReactBits)
- **What it is:** Animated scroll-triggered number counter.
- **Best for:** Stats, metrics, social proof.
- **Install:** `npx shadcn@latest add @react-bits/CountUp-TS-TW`

### RotatingText (ReactBits)
- **What it is:** Cycles through a word list in one text slot.
- **Best for:** Hero taglines with multiple value props.
- **Avoid when:** More than 4–5 words — users lose track.
- **Install:** `npx shadcn@latest add @react-bits/RotatingText-TS-TW`

### TrueFocus / TextPressure (ReactBits)
- **What it is:** Interactive text reacting to cursor proximity.
- **Best for:** Portfolio heroes, creative agency pages.
- **Avoid when:** Mobile-first contexts.
- **Install:** `npx shadcn@latest add @react-bits/TrueFocus-TS-TW`

---

## UI Components

### SpotlightCard (ReactBits)
- **What it is:** Radial spotlight that follows cursor on a card.
- **Best for:** Feature cards, pricing tiers, dark UI.
- **Install:** `npx shadcn@latest add @react-bits/SpotlightCard-TS-TW`

### TiltCard (ReactBits)
- **What it is:** Card tilts in 3D on hover.
- **Best for:** Product cards, portfolio, collectibles.
- **Avoid when:** `prefers-reduced-motion` — can cause motion sickness.
- **Install:** `npx shadcn@latest add @react-bits/Tilt-TS-TW`

### Magnet (ReactBits)
- **What it is:** Element magnetically attracts toward cursor.
- **Best for:** CTAs, social links, playful moments.
- **Install:** `npx shadcn@latest add @react-bits/Magnet-TS-TW`

### PixelCard (ReactBits)
- **What it is:** Pixel-scatter animation on hover.
- **Best for:** Gaming, retro aesthetic, creative portfolios.
- **Install:** `npx shadcn@latest add @react-bits/PixelCard-TS-TW`

### StarBorder (ReactBits)
- **What it is:** Animated star/sparkle orbiting the element border.
- **Best for:** Featured items, premium badges, CTAs.
- **Install:** `npx shadcn@latest add @react-bits/StarBorder-TS-TW`

### RippleButton (ReactBits)
- **What it is:** Material-style ripple effect on click.
- **Best for:** Consumer apps, mobile-first UI, action feedback.
- **Install:** `npx shadcn@latest add @react-bits/RippleButton-TS-TW`

### AnimatedList (ReactBits)
- **What it is:** List items animate in with spring stagger.
- **Best for:** Notification feeds, activity logs, dynamic lists.
- **Install:** `npx shadcn@latest add @react-bits/AnimatedList-TS-TW`

### Dock (ReactBits)
- **What it is:** macOS-style magnifying dock navigation.
- **Best for:** App-style interfaces, portfolio navigation, creative tools.
- **Install:** `npx shadcn@latest add @react-bits/Dock-TS-TW`

---

## Layout Patterns

Not just grids — visual layout systems that carry their own aesthetic meaning.

### Bento Grid
- **What it is:** An asymmetric grid of cards at different sizes (1×1, 1×2, 2×1, 2×2) arranged to create visual hierarchy and rhythm. Each card features a different content type.
- **Best for:** SaaS feature sections, portfolio overview, product landing pages, app store screenshots.
- **Avoid when:** The content items are uniform — bento only works when cards have genuinely different weights and story.
- **Color pairing:** Works with any palette — use the grid background as the base color and each card as a surface variant.

```css
.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: auto;
  gap: 16px;
}

/* Size variants */
.bento-1x1 { grid-column: span 1; grid-row: span 1; }
.bento-2x1 { grid-column: span 2; grid-row: span 1; }
.bento-1x2 { grid-column: span 1; grid-row: span 2; }
.bento-2x2 { grid-column: span 2; grid-row: span 2; }

/* Responsive collapse */
@media (max-width: 768px) {
  .bento-grid { grid-template-columns: repeat(2, 1fr); }
  .bento-2x2 { grid-column: span 2; }
  .bento-2x1 { grid-column: span 2; }
}
```

**Bento hierarchy rule:** The largest card (2×2) must contain the most important or most visually rich content. Never waste the biggest slot on supporting information.

### Infinite Scroll / Marquee (ReactBits)
- **What it is:** Continuously scrolling horizontal or vertical ticker — logos, testimonials, tags.
- **Best for:** Social proof logo strips, testimonial streams, tag clouds, brand partner sections.
- **Avoid when:** The content requires the user to read and act — marquees are for passive exposure, not interactive content.
- **Install:** `npx shadcn@latest add @react-bits/InfiniteScroll-TS-TW`

```css
/* Pure CSS marquee fallback */
.marquee-track {
  display: flex;
  width: max-content;
  animation: marquee 20s linear infinite;
}

@keyframes marquee {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}

/* Pause on hover */
.marquee-track:hover { animation-play-state: paused; }
```

### CircularGallery (ReactBits)
- **What it is:** Images or cards arranged in an interactive rotating circular track.
- **Best for:** Portfolio showcases, product galleries, team pages, creative brand moments.
- **Install:** `npx shadcn@latest add @react-bits/CircularGallery-TS-TW`

---

## Liquid & Glass FX

High-impact organic effects. Statement moments — use once per project.

> **Agent rule:** Liquid and glass effects are brand moments, not layout patterns. One use per project maximum.

### liquid-logo (paper-design)
- **Source:** [liquid-logo](https://github.com/paper-design/liquid-logo) — MIT
- **What it is:** Animated liquid morphing applied to a logo or SVG path.
- **Best for:** Hero logo reveals, premium product launches.
- **Avoid when:** Logo must stay static and recognizable at all times.

```tsx
import { LiquidLogo } from '@paper-design/liquid-logo'
// install: npm i @paper-design/liquid-logo

<LiquidLogo src="/logo.svg" speed={0.8} color="#D4AF37" />
```

### liquid-glass-js (dashersw)
- **Source:** [liquid-glass-js](https://github.com/dashersw/liquid-glass-js) — MIT
- **What it is:** Apple visionOS-inspired distortion + refraction shader on any DOM element.
- **Best for:** Premium hero UI, modal overlays, Apple-ecosystem product pages.
- **Avoid when:** Performance is tight or brand is not in the premium/Apple-adjacent space.

```tsx
import { LiquidGlass } from 'liquid-glass-js'
// install: npm i liquid-glass-js

<LiquidGlass>
  <div className="p-8"><h2>Premium feature</h2></div>
</LiquidGlass>
```

---

## 3D in UI

> **Agent rule:** Only suggest R3F when the brief explicitly requires 3D depth. Never default to R3F when ShaderGradient or CSS achieves the same result.

### react-three-fiber
- **Source:** [react-three-fiber](https://github.com/pmndrs/react-three-fiber) — MIT
- **What it is:** React renderer for Three.js.
- **Best for:** 3D product viewers, abstract 3D hero sections, interactive data visualizations.
- **Bundle note:** Three.js is ~600KB. Always code-split and lazy-load.

```tsx
import { Canvas } from '@react-three/fiber'
import { OrbitControls, MeshDistortMaterial } from '@react-three/drei'
// install: npm i @react-three/fiber @react-three/drei three

export function Hero3D() {
  return (
    <Canvas camera={{ position: [0, 0, 4] }}>
      <ambientLight intensity={0.5} />
      <directionalLight position={[10, 10, 5]} />
      <mesh>
        <sphereGeometry args={[1.5, 64, 64]} />
        <MeshDistortMaterial color="#4B2E83" distort={0.4} speed={1.5} roughness={0.2} />
      </mesh>
      <OrbitControls enableZoom={false} autoRotate />
    </Canvas>
  )
}
```

---

## Performance Tiers

| Tier | Effects | When to use |
|---|---|---|
| **Lightweight** | CSS animations, ShinyText, CountUp, FadeContent, DotGrid, Skeleton, Hover states, Gradient borders | Any project, including mobile-first |
| **Medium** | Aurora, Waves, BlurText, SplitText, SpotlightCard, ShaderGradient, Stagger, Page transitions | Controlled bundle size, modern device targets |
| **Heavy** | Ballpit, Hyperspeed, Particles, liquid-glass-js, TiltCard, Variable font animation | Landing pages, portfolio, launch pages — not product UI |
| **Maximum** | react-three-fiber, liquid-logo with complex SVG | Hero-only, code-split, static fallback mandatory |

---

## Accessibility Rules

- **Always respect `prefers-reduced-motion`.** Fall back to static content for all animations.
- **Neumorphism requires a contrast audit.** It almost always fails WCAG — verify before shipping.
- **Never animate body text** — headlines and decorative elements only.
- **Contrast applies at every frame.** Animated text must pass WCAG at every point in the animation.
- **Don't rely on motion to convey meaning** — content must work with animation disabled.
- **Focus states are non-negotiable.** Every interactive element needs a visible `:focus-visible` style.

```tsx
const prefersReducedMotion =
  window.matchMedia('(prefers-reduced-motion: reduce)').matches

{prefersReducedMotion ? <h1>{text}</h1> : <BlurText text={text} />}
```

---

## Color Bridge

This skill works alongside [color-combo-skill](https://github.com/bilioveloso/color-combo-skill). Always source colors from a named palette.

| Effect context | Recommended palette |
|---|---|
| AI/tech SaaS hero with ShaderGradient | Otherworldly or Soft Gradients |
| Dark gaming hero with Hyperspeed or Particles | Gaming / Esports |
| Premium brand hero with liquid-logo | Luxury |
| Wellness app with Aurora or Waves | Soft Gradients or Nature / Organic |
| Corporate dashboard with DotGrid | Corporate / Enterprise |
| Gothic editorial with shader or glass | Gothic / Dark Romance |
| Playful consumer with Ballpit or Claymorphism | Acid Contemporary or Warm Tropical / Resort |
| Brutalist developer tool | Acid Contemporary (black + electric yellow) |
| Neumorphic wellness app | Minimalist (Warm Mono) or soft Healthcare palettes |
| Bento grid SaaS section | Corporate / Enterprise or Luxury Facade |
| Animated gradient border on dark UI | Gaming / Esports or Otherworldly |
