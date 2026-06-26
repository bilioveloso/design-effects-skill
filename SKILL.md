---
name: design-effects-skill
description: >-
  Visual effects, animation patterns, morphism systems, interaction states, and
  layout patterns for UI and branding contexts. Use when choosing or
  implementing animated backgrounds, text effects, morphism styles,
  micro-interactions, motion patterns, cursor effects, image/media effects,
  liquid/glass FX, shader gradients, depth systems, border effects, scroll
  animations, dark-mode adaptations, or 3D elements. Activate on: "add animation",
  "make it more dynamic", "animated background", "text effect", "visual effect",
  "glassmorphism", "neumorphism", "claymorphism", "brutalism", "bento grid",
  "shader", "3D hero", "micro-interaction", "hover effect", "loading state",
  "gradient border", "lottie", "custom cursor", "image reveal", "scroll timeline",
  "page recipe", "saas landing", "portfolio", "gaming page", "wellness app",
  "/design-effects-skill".
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
  - lottie
  - custom cursor
  - image reveal
  - scroll timeline
  - dark mode motion
  - tooltip animation
  - drawer animation
  - page recipe
  - saas landing page
  - gaming landing page
  - wellness app
  - developer tool
  - creative portfolio
  - consumer app
  - dark editorial
  - enterprise dashboard
  - /design-effects-skill
author: bilioveloso
version: "3.1"
---

# Design Effects Skill

## Purpose
This skill teaches an agent to make strong, deliberate design-effect decisions — from choosing a morphism style to selecting the right animation primitive to knowing when restraint is the better design move. For any visual output requiring motion, depth, texture, or atmosphere, the agent should:

1. Identify the context, brand tier, and performance budget.
2. Check the Page-Type Recipes section first — if the project matches a known archetype, use that stack directly.
3. Use the Decision Guide to fill in any gaps or custom needs.
4. Pick the lightest effect that achieves the visual goal.
5. Apply the minimal code snippet as a starting point.
6. Cross-reference color-combo-skill for palette pairing.
7. Check accessibility, dark mode, and reduced-motion behavior before shipping.

## Core Rules
- **Never add effects for the sake of effects.** Every animation or visual style must serve atmosphere, feedback, hierarchy, or focus.
- **Performance first.** Heavy effects (3D, shaders, particles, distortion, liquid glass) belong on hero moments, not across the whole interface.
- **One hero effect per page.** If a page has a ShaderGradient hero, it does not also need Ballpit, neon borders, and liquid glass cards.
- **Mobile check.** Shader, 3D, and cursor-dependent effects often fail on mobile. Always provide a static or touch-friendly fallback.
- **Morphism needs a background.** Glass, clay, and neuo effects only work when the background provides contrast and context.
- **Neumorphism and accessibility are enemies.** Use only after a deliberate contrast audit, and usually only for decorative surfaces.
- **Dark mode changes the material system.** Shadows weaken, glows strengthen, borders need lower contrast, and glass opacity must change.
- **Color bridge.** Always source colors from [color-combo-skill](https://github.com/bilioveloso/color-combo-skill) instead of arbitrary hex choices.

---

## Page-Type Recipes

Each recipe is a complete, opinionated effect stack for a specific project archetype. Use these directly — don't mix stacks between archetypes.

> **Agent rule:** When a project clearly matches one of these archetypes, apply this recipe as the starting point. Only deviate when the brief explicitly calls for it.

---

### Recipe 1 — Premium AI / SaaS Landing Page

**Mood:** Intelligent, aspirational, modern dark premium.

| Layer | Choice | Notes |
|---|---|---|
| Hero background | ShaderGradient (`waterPlane`, `animate: on`) | Colors from Otherworldly or Dreamy Periwinkle palette |
| Hero text | BlurText or SplitText | One animated headline, everything else static |
| Card surface | Glassmorphism (standard or brand-tinted) | On a dark base — glass only works on rich background |
| Feature section | Bento Grid (2×2 hero card + smaller supporting) | SpotlightCard for hover interaction on each cell |
| Scroll reveals | IntersectionObserver + stagger (80ms offset) | Fade + translateY(20px) |
| Social proof | Infinite scroll marquee (logos) + CountUp (stats) | Marquee pauses on hover |
| Accent | Gradient border on primary CTA | Pseudo-element technique, animated spin optional |
| Typography | GradientText on subheadline label | Keep to one element — badge or eyebrow label |
| Page transition | Framer Motion fade + y:8 | 200ms ease-out |
| Mobile fallback | Static gradient background | Disable ShaderGradient on `max-width: 768px` |

**Palette:** Otherworldly, Dreamy Periwinkle, or Silver Pulse from color-combo-skill.

**Never use in this archetype:** Claymorphism, Brutalism, Ballpit, Hyperspeed, custom cursor on product pages.

---

### Recipe 2 — Gaming / Esports Launch Page

**Mood:** High-energy, cinematic, aggressive, neon-lit.

| Layer | Choice | Notes |
|---|---|---|
| Hero background | Hyperspeed or Particles | Dark base, high contrast |
| Hero text | GlitchText on title + SplitText on tagline | GlitchText only on brand name, never on body |
| Card surface | Dark glass + animated neon glow border | `border: 1px solid accent` + glow-pulse keyframe |
| Feature section | Scroll-snap horizontal gallery | Full-bleed cards, one per feature |
| Scroll reveals | Stagger entrance (60ms, faster than SaaS) | Faster tempo matches brand energy |
| CTA button | Spinning gradient border + colored shadow | Accent: Midnight Frag cyan or Neon Abyss green |
| Accent typography | Outlined stroke text as section background texture | Low opacity, oversized, pointer-events none |
| Loader | Custom animated SVG progress bar | On-brand color, no default spinner |
| Motion speed | Sharp easing (100–160ms), high stiffness spring | Snappy not smooth — gaming prefers crisp |
| Mobile fallback | Particles → static dark gradient with grain | Disable Hyperspeed on mobile unconditionally |

**Palette:** Gaming / Esports (Midnight Frag, Neon Abyss) or Acid Contemporary from color-combo-skill.

**Never use in this archetype:** Neumorphism, Claymorphism, soft Aurora, wellness colors, serif fonts.

---

### Recipe 3 — Wellness / Healthcare App

**Mood:** Calm, trustworthy, breathing, organic.

| Layer | Choice | Notes |
|---|---|---|
| Hero background | Aurora (slow, low saturation) or Waves | Never Hyperspeed, Particles, or ShaderGradient |
| Hero text | FadeContent or BlurText (slow, 200ms delay) | Never GlitchText or rapid SplitText |
| Card surface | Soft glassmorphism on light background | High blur, very low opacity — barely-there glass |
| Feature section | Stagger reveal grid (gentle, 120ms offset) | No Bento — keep layout calm and predictable |
| Scroll reveals | FadeContent only — no translate, no scale | Motion must be invisible as a technique |
| Social proof | Static testimonial cards with mask-reveal on scroll | No marquee — scrolling content feels rushed |
| CTA button | Full states (hover lift, active press) | No glow, no spinning border — clean and trusted |
| Empty states | Lottie illustration (calm loop) | Never use a spinner alone in an empty state |
| Icon animation | SVG stroke draw on success confirmations | Checkmark draw, circle draw — reassuring feedback |
| Motion timing | Ease-out, 250–400ms, never under 180ms | Slow timing = calm = trusted |

**Palette:** Nature / Organic (Eucalyptus Glow), Healthcare (Clinical Clarity, Vital Green), or Soft Gradients from color-combo-skill.

**Never use in this archetype:** GlitchText, Hyperspeed, Ballpit, Brutalism, Neumorphism, neon borders.

---

### Recipe 4 — Developer Tool / Open Source

**Mood:** Precise, no-nonsense, functional with personality.

| Layer | Choice | Notes |
|---|---|---|
| Hero background | DotGrid (animated, subtle) or ShaderGradient (monochrome) | Low energy background — the code content is the hero |
| Hero text | SplitText or plain — never over-animated | Developers respect restraint; distrust heavy effects |
| Card surface | Brutalism accents OR flat dark surface with gradient border | Not both — pick one material language |
| Feature section | Bento Grid or plain responsive grid | SpotlightCard acceptable on dark UI feature cells |
| Scroll reveals | IntersectionObserver, translateY only, 0.3s | Fast and clean — not dramatic |
| Code blocks | Syntax-highlighted, ShinyText for copy-to-clipboard badge | No animation on the code itself |
| CTA button | Brutalist offset shadow OR subtle glow — not both | Match the card language chosen above |
| Terminal/CLI moment | Animated SVG stroke for typing cursor effect | Draws developer attention immediately |
| Social proof | CountUp for GitHub stars, npm downloads, users | Hard numbers land better than testimonials |
| Motion timing | Sharp easing (120–200ms) | Tool-like tempo |

**Palette:** Acid Contemporary, Minimalist (Bone & Carbon), or Corporate (Steel Authority) from color-combo-skill.

**Never use in this archetype:** Ballpit, Hyperspeed, Claymorphism, heavy 3D, Aurora, Waves.

---

### Recipe 5 — Creative Portfolio / Agency

**Mood:** High-personality, experimental, one-of-a-kind.

| Layer | Choice | Notes |
|---|---|---|
| Hero background | ShaderGradient or full-bleed editorial photography | If photography: grain overlay + blend mode for texture |
| Cursor | Custom cursor dot with `mix-blend-mode: difference` | Only on desktop — hide on touch devices |
| Hero text | Variable font weight animation on hover OR SplitText | One technique only — not both |
| Card surface | Image zoom + overlay — no morphism | Let the work speak; morphism competes with the content |
| Project grid | Masonry or asymmetric CSS grid | CircularGallery or Scroll-snap horizontal gallery |
| Scroll reveals | Mask reveal (clip-path wipe) on each project image | Left-to-right or bottom-to-top wipe |
| Page transitions | Framer Motion — full cover wipe or opacity crossfade | Adds brand identity at the route level |
| Typography | Outlined stroke text as section label or background texture | One instance — not every section |
| Accent | liquid-logo on logo reveal OR gradient border on CTA | One statement liquid/glass moment total |
| Motion timing | Premium ease cubic-bezier(0.22, 1, 0.36, 1), 400–600ms | Slower and more deliberate = premium craft |

**Palette:** Any — but pick one and commit. Luxury, Gothic / Dark Romance, and Acid Contemporary all work at this tier.

**Never use in this archetype:** Skeleton loaders, enterprise grids, standard button libraries, default browser cursors on desktop.

---

### Recipe 6 — Consumer Lifestyle App

**Mood:** Warm, energetic, tactile, approachable.

| Layer | Choice | Notes |
|---|---|---|
| Hero background | Aurora (warm tones) or static gradient with grain | Ballpit acceptable for playful onboarding moment only |
| Hero text | BlurText or RotatingText (max 4 words) | Friendly and readable, not aggressive |
| Card surface | Claymorphism (light background only) | Inflated, colorful, tactile — matches lifestyle brand |
| Feature section | Stagger grid with clay cards | 100ms offset, translateY(12px) |
| Scroll reveals | FadeContent or ScrollReveal | Gentle, not dramatic |
| Social proof | CountUp + Marquee testimonials | Warm social proof — reviews, not metrics |
| CTA button | Clay button style with press state | Inner highlight + offset shadow for clay feel |
| Onboarding | Lottie illustrations for each step | Playful, branded, non-generic |
| Icon animation | Bouncy SVG icons (spring physics, scale 0.9→1.1→1) | Matches the playful material language |
| Motion timing | Spring (medium stiffness, medium damping) + ease-out | Approachable and bouncy, not corporate |

**Palette:** Warm Tropical / Resort, Soft Gradients (Peach Champagne, Dreamy Periwinkle), or Luxury Facade from color-combo-skill.

**Never use in this archetype:** Brutalism, heavy 3D, GlitchText, dark glass, enterprise grids.

---

### Recipe 7 — Dark Editorial / Magazine

**Mood:** Cinematic, high contrast, still, atmospheric.

| Layer | Choice | Notes |
|---|---|---|
| Hero background | Full-bleed photography + grain overlay + dark scrim | No animated background — image IS the hero |
| Grain | Grain overlay at 6–10% opacity, `mix-blend-mode: overlay` | Applied to every section, not just hero |
| Hero text | Oversized display type — possibly outlined/stroke | Static or slow fade-in — never spring or glitch |
| Card surface | Glassmorphism (dark tinted) on editorial image cards | Image zoom on hover underneath glass |
| Section dividers | Mask-reveal wipe as content transitions in | Horizontal wipe, 0.8s ease-out |
| Typography detail | Variable font hover on article titles | Subtle weight shift on hover — 300 → 700 |
| Accent | Gradient border (muted, low saturation) on featured item | One per page |
| Body motion | FadeContent only | Never animate body copy |
| Social / sharing | ShinyText on "New" or "Featured" badge | Minimal — one accent per page |
| Motion timing | Premium ease, 400–700ms, always ease-out | Long, deliberate, cinematic |

**Palette:** Gothic / Dark Romance (Velvet Crypt, Blood Amber), Luxury, or Minimalist (Bone & Carbon) from color-combo-skill.

**Never use in this archetype:** Claymorphism, Ballpit, Particles, CountUp, Hyperspeed, Marquee.

---

### Recipe 8 — Enterprise Dashboard / B2B SaaS

**Mood:** Trusted, efficient, precise, data-forward.

| Layer | Choice | Notes |
|---|---|---|
| Background | Flat dark or flat light — no animated background in app shell | DotGrid acceptable on marketing/login page only |
| Hero / onboarding | FadeContent or ScrollReveal on first login | Welcome state only — never in everyday dashboard |
| Card surface | Flat with elevation shadow system (Level 1–2 only) | No morphism in data-heavy contexts |
| Data visualization | Stagger entrance on charts (bars animate in sequentially) | CountUp on KPI metrics |
| Loading states | Shimmer skeleton (matches card layout exactly) | Never use a full-page spinner in a dashboard |
| Interactions | Full button states — hover, active, focus-visible, disabled | Non-negotiable; must pass WCAG |
| Modals / drawers | Drawer slide-in (translateX), modal fade+scale(0.98→1) | 220–280ms, ease-out |
| Notification feed | AnimatedList (spring stagger) | Makes real-time updates feel live without noise |
| Tooltips | Fade + translateY(4px), 160ms | Fast — never block workflow |
| Motion timing | Soft ease-out (200–280ms) — purposeful but invisible | Motion should never be the thing users notice |

**Palette:** Corporate / Enterprise (Steel Authority, Slate Command), Minimalist, or Soft Gradients (light mode) from color-combo-skill.

**Never use in this archetype:** ShaderGradient in UI shell, Hyperspeed, Ballpit, Claymorphism, custom cursors, Brutalism, heavy text animations.

---

## Decision Guide

### By goal

| Goal | Effect / Category |
|---|---|
| Immersive hero background | Animated Backgrounds → ShaderGradient or Aurora |
| Subtle atmospheric texture | Animated Backgrounds → DotGrid, Noise, Grain |
| High-energy launch moment | Animated Backgrounds → Hyperspeed |
| Hero text reveal | Text Animations → BlurText or SplitText |
| Scroll-triggered content entrance | Motion & Scroll → ScrollReveal, Stagger, or Scroll Timeline |
| Metrics and social proof | Text Animations → CountUp |
| Strong card hierarchy | Layout Patterns → Bento Grid |
| Premium frosted surface | Design Morphisms → Glassmorphism |
| Soft tactile surface | Design Morphisms → Neumorphism |
| Playful inflated surface | Design Morphisms → Claymorphism |
| Raw anti-polish aesthetic | Design Morphisms → Brutalism |
| Product feedback state | Micro-interactions → Success / Error / Loading |
| Premium image reveal | Image & Media Effects → Mask Reveal or Hover Distortion |
| Brand logo motion | Icon & SVG Animation → SVG stroke animation or liquid-logo |
| Portfolio cursor drama | Cursor Effects → Crosshair / Custom Cursor |
| Navigation or overlay entrance | UI Motion Patterns → Drawer, Tooltip, Dropdown |
| Horizontal showcase layout | Layout Patterns → Scroll Snap or Horizontal Scroll |
| 3D product or hero | 3D in UI → react-three-fiber |

### By animation primitive

| Need | Best primitive |
|---|---|
| Simple hover state | CSS transition |
| Repeated decorative loop | CSS keyframes |
| Scroll-linked entrance | IntersectionObserver + CSS |
| Scroll position drives progress | CSS `animation-timeline: scroll()` or JS scroll sync |
| Route/page transitions | Framer Motion |
| SVG line drawing | `stroke-dasharray` / `stroke-dashoffset` |
| Complex illustration animation | Lottie |
| Physically believable UI motion | Spring physics |
| 3D scene / mesh / shader | react-three-fiber or ShaderGradient |

---

## Design Morphisms

Morphism styles define the material language of surfaces and cards. Choose one per project and apply it consistently.

> **Agent rule:** Never mix morphism styles in the same interface. Glass next to neumorphic controls next to brutalist cards is design indecision, not richness.

### Glassmorphism
- **What it is:** Frosted translucent surface using `backdrop-filter` blur, usually paired with subtle border and soft shadow.
- **Best for:** Premium overlays, nav bars on hero images, modal shells, dashboard highlights.
- **Avoid when:** The background is flat, the UI is dense, or readability is more important than atmosphere.

```css
.glass-card {
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(20px) saturate(180%);
  -webkit-backdrop-filter: blur(20px) saturate(180%);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 16px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
}

.glass-card--dark {
  background: rgba(0, 0, 0, 0.35);
  backdrop-filter: blur(24px) saturate(160%);
  -webkit-backdrop-filter: blur(24px) saturate(160%);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 12px;
}
```

### Neumorphism
- **What it is:** Soft raised or inset surfaces created with paired light and dark shadows on a same-color background.
- **Best for:** Decorative wellness surfaces, audio players, tactile widgets.
- **Avoid when:** Controls need strong clarity, contrast, or enterprise credibility.

```css
.neuo-raised {
  background: #E8E0D8;
  border-radius: 16px;
  box-shadow:
    8px 8px 16px rgba(0, 0, 0, 0.15),
    -8px -8px 16px rgba(255, 255, 255, 0.7);
}
```

### Claymorphism
- **What it is:** Inflated rounded surfaces with chunky shadows, inner highlights, and toy-like tactility.
- **Best for:** Playful mobile onboarding, consumer apps, lifestyle brands.
- **Avoid when:** Professional trust is the main goal.

```css
.clay-card {
  background: #FFD3B6;
  border-radius: 28px;
  box-shadow:
    0 8px 0px rgba(0, 0, 0, 0.15),
    0 16px 40px rgba(0, 0, 0, 0.12),
    inset 0 -4px 8px rgba(0, 0, 0, 0.08),
    inset 0 4px 8px rgba(255, 255, 255, 0.6);
}
```

### Brutalism
- **What it is:** Flat color, hard borders, offset shadows, intentional roughness, no softness.
- **Best for:** Developer tools, editorial, creative agencies, anti-corporate brands.
- **Avoid when:** Safety, polish, and reassurance matter more than personality.

```css
.brutal-card {
  background: #F5E800;
  border: 3px solid #0A0A0A;
  border-radius: 0;
  box-shadow: 6px 6px 0px #0A0A0A;
  padding: 24px;
}
```

---

## Micro-interactions

Micro-interactions communicate response, affordance, and confidence. They are the difference between a UI feeling static versus alive.

> **Agent rule:** Every interactive element needs hover, active, focus-visible, and disabled or inactive behavior.

### Button States
```css
.button {
  background: #2A7AE8;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 12px 24px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s ease, transform 0.1s ease, box-shadow 0.15s ease;
}
.button:hover {
  background: #4A90F0;
  box-shadow: 0 4px 16px rgba(42, 122, 232, 0.35);
  transform: translateY(-1px);
}
.button:active {
  background: #1A5AB8;
  transform: translateY(1px);
  box-shadow: none;
}
.button:focus-visible {
  outline: 3px solid #2A7AE8;
  outline-offset: 3px;
}
.button:disabled {
  background: #A8B8CC;
  cursor: not-allowed;
}
```

### Loading States
| Use | When |
|---|---|
| Skeleton | Layout shape is known |
| Spinner | Short inline action or unknown wait |
| Progress bar | Completion percentage is known |
| Shimmer skeleton | Preferred when keeping layout stable |

### Success / Error State Animation
```css
@keyframes success-pulse {
  0% { box-shadow: 0 0 0 0 rgba(26, 138, 64, 0.4); }
  70% { box-shadow: 0 0 0 10px rgba(26, 138, 64, 0); }
  100% { box-shadow: 0 0 0 0 rgba(26, 138, 64, 0); }
}
.state-success { animation: success-pulse 0.6s ease-out; }

@keyframes error-shake {
  0%,100% { transform: translateX(0); }
  20% { transform: translateX(-6px); }
  40% { transform: translateX(6px); }
  60% { transform: translateX(-4px); }
  80% { transform: translateX(4px); }
}
.state-error { animation: error-shake 0.4s ease-out; }
```

### Hover Reveal Patterns
```css
.link-underline { position: relative; text-decoration: none; }
.link-underline::after {
  content: '';
  position: absolute;
  left: 0; bottom: -2px;
  width: 0; height: 2px;
  background: currentColor;
  transition: width 0.25s ease;
}
.link-underline:hover::after { width: 100%; }
```

---

## Typography Effects

Typography can act as content, structure, and visual atmosphere simultaneously.

### Variable Font Animations
```css
.variable-headline {
  font-family: 'Inter Variable', sans-serif;
  font-variation-settings: 'wght' 300;
  transition: font-variation-settings 0.3s ease;
}
.variable-headline:hover { font-variation-settings: 'wght' 800; }
```

### Outlined / Stroke Text
```css
.text-outline {
  -webkit-text-stroke: 2px #0A0A0A;
  color: transparent;
  font-size: clamp(4rem, 10vw, 10rem);
  font-weight: 900;
}
```

### Oversized Display Texture
```css
.display-texture {
  position: absolute;
  font-size: clamp(8rem, 20vw, 20rem);
  font-weight: 900;
  opacity: 0.04;
  pointer-events: none;
  user-select: none;
}
```

### Gradient Text Fill
```css
.gradient-text {
  background: linear-gradient(90deg, #B8C0FF, #E7D8FF, #D6C6F7, #B8C0FF);
  background-size: 200% auto;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient-flow 3s linear infinite;
}
@keyframes gradient-flow {
  0% { background-position: 0% center; }
  100% { background-position: 200% center; }
}
```

---

## Icon & SVG Animation

Animated icons are one of the most common product-level motion needs. They are small, expressive, and often lighter than full libraries.

> **Agent rule:** Use icon animation for state change and delight, not constant decoration. Repeating icon loops become visual noise fast.

### SVG Stroke Drawing
```css
.path-draw {
  stroke-dasharray: 400;
  stroke-dashoffset: 400;
  animation: draw 1.2s ease forwards;
}

@keyframes draw {
  to { stroke-dashoffset: 0; }
}
```

### Lottie
- **What it is:** JSON-based vector animation exported from After Effects, rendered with a lightweight player.
- **Best for:** Product onboarding, empty states, success states, branded explainer moments.
- **Avoid when:** A simple SVG or CSS animation would do.

```tsx
import Lottie from 'lottie-react'
import successAnimation from './success.json'

<Lottie animationData={successAnimation} loop={false} />
```

---

## Cursor Effects

Cursor design is a high-personality layer — powerful in portfolios and brand experiences, usually wrong for product UI.

> **Agent rule:** Cursor effects are desktop-only enhancements. Never rely on them for meaning, affordance, or navigation.

### Custom Cursor Dot
```css
.custom-cursor {
  position: fixed;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #D4AF37;
  pointer-events: none;
  mix-blend-mode: difference;
  transform: translate(-50%, -50%);
  z-index: 9999;
}
```

```tsx
useEffect(() => {
  const move = (e: MouseEvent) => {
    if (cursorRef.current) {
      cursorRef.current.style.left = `${e.clientX}px`
      cursorRef.current.style.top = `${e.clientY}px`
    }
  }
  window.addEventListener('mousemove', move)
  return () => window.removeEventListener('mousemove', move)
}, [])
```

---

## Image & Media Effects

### Mask Reveal on Scroll
```css
.image-reveal {
  clip-path: inset(0 100% 0 0);
  animation: reveal 0.8s ease-out forwards;
}

@keyframes reveal {
  to { clip-path: inset(0 0 0 0); }
}
```

### Image Zoom + Overlay
```css
.media-card { position: relative; overflow: hidden; }
.media-card img { transition: transform 0.5s ease; }
.media-card::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.45), rgba(0,0,0,0));
  opacity: 0;
  transition: opacity 0.3s ease;
}
.media-card:hover img { transform: scale(1.06); }
.media-card:hover::after { opacity: 1; }
```

### Grain / Noise Texture
```css
.grain-overlay::before {
  content: '';
  position: absolute;
  inset: 0;
  opacity: 0.08;
  pointer-events: none;
  background-image:
    radial-gradient(circle at 20% 20%, rgba(255,255,255,0.4) 0.5px, transparent 0.5px),
    radial-gradient(circle at 80% 80%, rgba(0,0,0,0.4) 0.5px, transparent 0.5px);
  background-size: 4px 4px;
  mix-blend-mode: overlay;
}
```

---

## Easing & Spring Reference

| Feel | Use | Timing |
|---|---|---|
| **Ease-out** | Most UI entrances, hover lifts, content reveal | 180–300ms |
| **Ease-in-out** | Balanced loops, panels | 250–400ms |
| **Linear** | Marquee, progress bars, loops | continuous |
| **Spring** | Cards, toggles, playful elements | tuned by stiffness/damping |
| **Sharp / snap** | Brutalist interactions, tool UIs | 100–180ms |

```css
--ease-premium: cubic-bezier(0.22, 1, 0.36, 1);
--ease-soft:    cubic-bezier(0.25, 0.1, 0.25, 1);
--ease-snap:    cubic-bezier(0.2, 0.8, 0.2, 1);
```

---

## Motion & Scroll

### IntersectionObserver Reveal
```tsx
useEffect(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) entry.target.classList.add('in-view')
    })
  }, { threshold: 0.2 })

  document.querySelectorAll('.reveal').forEach((el) => observer.observe(el))
  return () => observer.disconnect()
}, [])
```

```css
.reveal {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s var(--ease-premium), transform 0.5s var(--ease-premium);
}
.reveal.in-view { opacity: 1; transform: translateY(0); }
```

### CSS Scroll-Driven Animations
```css
@supports (animation-timeline: scroll()) {
  .scroll-progress {
    animation: grow linear both;
    animation-timeline: scroll();
    animation-range: 0% 100%;
    transform-origin: left center;
  }
  @keyframes grow {
    from { transform: scaleX(0); }
    to { transform: scaleX(1); }
  }
}
```

### Page Transitions
```tsx
import { AnimatePresence, motion } from 'framer-motion'

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

---

## Animated Backgrounds

### ShaderGradient
```tsx
import { ShaderGradientCanvas, ShaderGradient } from '@shadergradient/react'

export function HeroBackground() {
  return (
    <ShaderGradientCanvas style={{ position: 'absolute', inset: 0 }} pixelDensity={1.5} fov={45}>
      <ShaderGradient
        type="waterPlane"
        animate="on"
        uSpeed={0.3}
        uStrength={3}
        uDensity={1.2}
        color1="#B8C0FF"
        color2="#E7D8FF"
        color3="#1A0A1E"
        lightType="3d"
        brightness={1.2}
        grain="on"
      />
    </ShaderGradientCanvas>
  )
}
```

### Other background types
- **Aurora** — calm, premium, wellness-friendly.
- **Particles / Orbs** — AI, tech, dark UI hero sections.
- **Hyperspeed** — gaming and cinematic launch moments only.
- **Ballpit** — playful, youthful products.
- **DotGrid** — SaaS, tools, understated structure.
- **Waves** — fintech, wellness, tropical softness.

---

## UI Motion Patterns

### Tooltip Entrance
```css
.tooltip {
  opacity: 0;
  transform: translateY(4px) scale(0.98);
  transition: opacity 0.16s var(--ease-soft), transform 0.16s var(--ease-soft);
}
.tooltip[data-open="true"] {
  opacity: 1;
  transform: translateY(0) scale(1);
}
```

### Dropdown Menu
```css
.dropdown {
  opacity: 0;
  transform: translateY(-4px);
  transition: opacity 0.18s var(--ease-soft), transform 0.18s var(--ease-soft);
}
.dropdown[data-open="true"] {
  opacity: 1;
  transform: translateY(0);
}
```

### Drawer / Sheet
```css
.drawer {
  transform: translateX(100%);
  transition: transform 0.28s var(--ease-premium);
}
.drawer[data-open="true"] {
  transform: translateX(0);
}
```

---

## Layout Patterns

### Bento Grid
```css
.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
}
.bento-1x1 { grid-column: span 1; }
.bento-2x1 { grid-column: span 2; }
.bento-1x2 { grid-column: span 1; }
.bento-2x2 { grid-column: span 2; }
```

### Scroll Snap Gallery
```css
.snap-x {
  display: flex;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
}
.snap-item {
  flex: 0 0 100%;
  scroll-snap-align: start;
}
```

### Infinite Scroll / Marquee
```css
.marquee-track {
  display: flex;
  width: max-content;
  animation: marquee 20s linear infinite;
}
@keyframes marquee {
  from { transform: translateX(0); }
  to { transform: translateX(-50%); }
}
```

---

## Dark Mode Adaptations

- Shadows weaken in dark mode; use glow or subtle borders instead.
- Glass opacity should increase slightly for readability.
- Gradient borders need lower saturation in dark contexts.
- Grain texture works at lower opacity in dark mode.
- Always add a dark scrim on text over animated backgrounds.

```css
.dark .glass-card {
  background: rgba(10, 12, 16, 0.45);
  border-color: rgba(255, 255, 255, 0.08);
}
.dark .card-shadow {
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.45);
}
```

---

## 3D in UI

### react-three-fiber
```tsx
import { Canvas } from '@react-three/fiber'
import { OrbitControls, MeshDistortMaterial } from '@react-three/drei'

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
| **Lightweight** | CSS transitions, simple keyframes, hover states, tooltip/dropdown motion, stroke SVG animation, DotGrid | Any project |
| **Medium** | Aurora, BlurText, SplitText, ShaderGradient, IntersectionObserver reveals, Bento, scroll snap | Modern products with controlled bundle size |
| **Heavy** | Ballpit, Hyperspeed, Particles, Lottie, liquid-glass-js, custom cursors, variable font motion | Landing pages, creative work, launches |
| **Maximum** | react-three-fiber, liquid-logo with complex SVG, stacked hero effects | Hero-only, code-split, fallback mandatory |

---

## Accessibility Rules

- Respect `prefers-reduced-motion` for all animated systems.
- Do not rely on cursor effects for meaning.
- Neumorphism requires a contrast audit.
- Animated text must remain readable at every frame.
- Every interactive element needs visible `:focus-visible` states.
- Tooltip, dropdown, and drawer motion must not delay usability.

```tsx
const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches
```

---

## Color Bridge

Use [color-combo-skill](https://github.com/bilioveloso/color-combo-skill) for all color decisions.

| Context | Recommended palette |
|---|---|
| Premium AI SaaS hero | Otherworldly or Dreamy Periwinkle |
| Gaming glow borders | Gaming / Esports (Midnight Frag, Neon Abyss) |
| Wellness aurora layout | Nature / Organic or Healthcare |
| Dark editorial grain and glass | Gothic / Dark Romance |
| Corporate motion dashboard | Corporate / Enterprise |
| Brutalist developer tool | Acid Contemporary |
| Consumer lifestyle app | Warm Tropical / Resort or Soft Gradients |
| Creative portfolio | Any — one palette, committed |
