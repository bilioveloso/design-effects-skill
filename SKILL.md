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
  - /design-effects-skill
author: bilioveloso
version: "3.0"
---

# Design Effects Skill

## Purpose
This skill teaches an agent to make strong, deliberate design-effect decisions — from choosing a morphism style to selecting the right animation primitive to knowing when restraint is the better design move. For any visual output requiring motion, depth, texture, or atmosphere, the agent should:

1. Identify the context, brand tier, and performance budget.
2. Use the Decision Guide to match to an effect category.
3. Pick the lightest effect that achieves the visual goal.
4. Apply the minimal code snippet as a starting point.
5. Cross-reference color-combo-skill for palette pairing.
6. Check accessibility, dark mode, and reduced-motion behavior before shipping.

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
Use for line illustrations, logo reveals, signatures, or checkmarks.

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

### Animated Checkmark
```svg
<svg width="64" height="64" viewBox="0 0 64 64" fill="none">
  <circle cx="32" cy="32" r="30" stroke="#1A8A40" stroke-width="4" class="path-draw" />
  <path d="M18 33L28 43L46 23" stroke="#1A8A40" stroke-width="4" stroke-linecap="round" stroke-linejoin="round" class="path-draw" />
</svg>
```

### Lottie
- **What it is:** JSON-based vector animation format exported from After Effects, rendered with a lightweight player.
- **Best for:** Product onboarding, illustration loops, empty states, success states, branded explainer moments.
- **Avoid when:** A simple SVG or CSS animation would do — Lottie is for richer illustration motion, not basic hover states.

```tsx
import Lottie from 'lottie-react'
import successAnimation from './success.json'

<Lottie animationData={successAnimation} loop={false} />
```

---

## Cursor Effects

Cursor design is a high-personality layer. It is powerful in portfolios and brand experiences, but often wrong for product UI.

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

### Crosshair / Precision Cursor
- **Best for:** Portfolios, photography sites, creative tools, premium product showcases.
- **Avoid when:** The UI is task-heavy or cursor replacement would hurt familiarity.

---

## Image & Media Effects

Images often need motion more than text does. Image treatment defines brand polish quickly.

### Mask Reveal on Scroll
Use clip-path or transform-based reveals to make media enter elegantly.

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
.media-card {
  position: relative;
  overflow: hidden;
}
.media-card img {
  transition: transform 0.5s ease;
}
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
Grain adds tactility to flat backgrounds, gradients, glass, and editorial layouts.

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

### Blend Mode Layer
```css
.blend-accent {
  mix-blend-mode: screen;
  opacity: 0.7;
}
```

---

## Easing & Spring Reference

Motion feel matters as much as motion type. Picking the wrong easing curve can make premium UI feel cheap.

| Feel | Use | Timing |
|---|---|---|
| **Ease-out** | Most UI entrances, hover lifts, content reveal | 180–300ms |
| **Ease-in-out** | Balanced loop, subtle transitions, panels | 250–400ms |
| **Linear** | Marquee, progress bars, background loops | continuous |
| **Spring** | Physical cards, toggles, playful elements | tuned by stiffness/damping |
| **Sharp / snap** | Brutalist interactions, crisp tool UIs | 100–180ms |

### Recommended cubic-bezier curves
```css
/* Premium smooth */
--ease-premium: cubic-bezier(0.22, 1, 0.36, 1);

/* Soft standard UI */
--ease-soft: cubic-bezier(0.25, 0.1, 0.25, 1);

/* Snappy brutal / tool UI */
--ease-snap: cubic-bezier(0.2, 0.8, 0.2, 1);
```

### Spring guidance
- Use springs for drag, toggles, cards, cursors, and playful UI.
- Avoid springs for text readability reveals and dense dashboard transitions.
- High stiffness + low damping = energetic / playful.
- Medium stiffness + medium damping = premium / calm.

---

## Motion & Scroll

### ScrollReveal
- Use IntersectionObserver for performant viewport-driven reveals when libraries are unnecessary.

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
.reveal.in-view {
  opacity: 1;
  transform: translateY(0);
}
```

### CSS Scroll-Driven Animations
Use the native scroll timeline API when supported.

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

### Parallax
```css
.parallax-section {
  background-attachment: fixed;
  background-position: center;
  background-size: cover;
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

These are the bread-and-butter patterns of modern UI transitions.

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
Use for full-screen stories, product showcases, and horizontal feature tours.

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

### Sticky Hero Anatomy
A premium landing page often uses:
- Sticky hero copy
- Scrolling visual panel
- Parallax or reveal behind it
- Single primary CTA and one secondary CTA

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

Effects need different tuning in dark UI.

- Shadows should be weaker; use glow or border contrast instead.
- Glass opacity should increase slightly in dark mode for readability.
- Gradient borders need less saturation and lower luminance contrast.
- Grain works better at lower opacity in dark mode.
- White text on animated backgrounds needs a dark overlay or scrim.

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
| Premium glass hero | Luxury or Soft Gradients |
| Brutalist developer tool | Acid Contemporary |
| Claymorphic consumer app | Warm Tropical / Resort or Soft Gradients |
| Gaming glow borders | Gaming / Esports or Otherworldly |
| Wellness aurora layout | Nature / Organic or Healthcare |
| Dark editorial grain and glass | Gothic / Dark Romance |
| Corporate motion dashboard | Corporate / Enterprise |
