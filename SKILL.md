---
name: design-effects-skill
description: >-
  Visual effects and animation patterns for UI and branding contexts. Use when
  choosing or implementing animated backgrounds, text effects, motion patterns,
  liquid/glass FX, shader gradients, or 3D elements. Activate on: "add animation",
  "make it more dynamic", "animated background", "text effect", "visual effect",
  "glassmorphism", "shader", "3D hero", "/design-effects-skill".
trigger_keywords:
  - animation
  - animated background
  - text effect
  - visual effect
  - glassmorphism
  - liquid glass
  - shader gradient
  - motion
  - 3D UI
  - particle background
  - scroll animation
  - /design-effects-skill
author: bilioveloso
version: "1.0"
---

# Design Effects Skill

## Purpose
This skill teaches an agent to make better visual effect decisions by providing curated, categorized effects grouped by type and use case. For any visual output requiring motion, depth, or atmosphere, the agent should:

1. Identify the context and performance budget.
2. Use the Decision Guide to match to an effect category.
3. Pick the named effect that fits.
4. Apply the minimal code snippet.
5. Cross-reference color-combo-skill for palette pairing.

## Core Rules
- **Never add effects for the sake of effects.** Every animation must serve a purpose — atmosphere, feedback, or focus.
- **Performance first.** Heavy effects (3D, shaders, particles) are only justified on hero sections or dedicated visual moments, never on every element.
- **One hero effect per page.** If a page has a ShaderGradient hero, it doesn't also need a particle background and a liquid glass card.
- **Mobile check.** Shader and 3D effects can be expensive on mobile. Always provide a static fallback color or gradient.
- **Color bridge.** When choosing colors for any effect, reference [color-combo-skill](https://github.com/bilioveloso/color-combo-skill) palettes rather than picking arbitrary hex values.

## Decision Guide

| Goal | Effect category |
|---|---|
| Immersive, breathing hero background | Animated Backgrounds → ShaderGradient or Plasma Wave |
| Premium, flowing abstract background | Animated Backgrounds → Aurora or Gradient effects |
| Subtle, textured background | Animated Backgrounds → Dots, Grid, or Noise |
| Interactive particle atmosphere | Animated Backgrounds → Particle / Orb effects |
| Hero text that demands attention | Text Animations → SplitText, BlurText, or ShinyText |
| Counting numbers or stats | Text Animations → CountUp |
| Scroll-triggered reveals | Motion & Scroll → ScrollReveal, FadeContent |
| Hover micro-interactions | UI Components → Magnet, TiltCard, SpotlightCard |
| Premium brand logo animation | Liquid & Glass FX → liquid-logo |
| Apple-style frosted glass UI | Liquid & Glass FX → liquid-glass-js |
| Glassmorphism card or panel | UI Components → GlassCard or manual backdrop-filter |
| 3D product or abstract hero | 3D in UI → react-three-fiber |
| Animated gradient background (lightweight) | Animated Backgrounds → MeshGradient or CSS gradient animation |

---

## Animated Backgrounds

Use for hero sections, full-page backgrounds, and section transitions. These set the emotional atmosphere. Choose based on performance budget and brand mood.

> **Agent rule:** Animated backgrounds are for one dominant section only. Do not stack two animated backgrounds on the same page.

### ShaderGradient
- **Source:** [@shadergradient/react](https://github.com/ruucm/shadergradient) — MIT
- **What it is:** 3D animated mesh gradient rendered via WebGL/Three.js. Smooth, organic, endlessly customizable.
- **Best for:** AI/tech SaaS hero sections, premium landing pages, editorial digital products.
- **Avoid when:** Performance is constrained, users are likely on low-end mobile, or the page already has heavy JS.
- **Color pairing:** Use `color1`, `color2`, `color3` props. Map to Soft Gradients or Luxury palettes from color-combo-skill.

```tsx
import { ShaderGradientCanvas, ShaderGradient } from '@shadergradient/react'

// install: npm i @shadergradient/react @react-three/fiber three three-stdlib camera-controls

export function HeroBackground() {
  return (
    <ShaderGradientCanvas
      style={{ position: 'absolute', inset: 0 }}
      pixelDensity={1.5}
      fov={45}
    >
      <ShaderGradient
        type="waterPlane"
        animate="on"
        uSpeed={0.3}
        uStrength={3}
        uDensity={1.2}
        color1="#B8C0FF"  // Dreamy Periwinkle — Soft Gradients
        color2="#E7D8FF"
        color3="#1A0A1E"  // Velvet Crypt — Gothic / Dark Romance
        lightType="3d"
        brightness={1.2}
        grain="on"
      />
    </ShaderGradientCanvas>
  )
}
```

**Static fallback (mobile):**
```css
.hero-bg-fallback {
  background: linear-gradient(135deg, #B8C0FF 0%, #E7D8FF 100%);
}
```

### Ballpit (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/backgrounds/ballpit) — MIT
- **What it is:** Physics-based bouncing 3D balls filling a container. Playful, interactive.
- **Best for:** Playful SaaS, gaming, youthful consumer products, interactive hero moments.
- **Avoid when:** The brand is serious, corporate, or minimal.
- **Color pairing:** Acid Contemporary or Gaming/Esports palettes.
- **Install:** `npx shadcn@latest add @react-bits/Ballpit-TS-TW`

### Aurora (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/backgrounds/aurora) — MIT
- **What it is:** Soft animated aurora borealis gradient background. CSS/canvas based, lightweight.
- **Best for:** Wellness, premium digital, calm SaaS, editorial.
- **Avoid when:** High energy or dark gaming contexts.
- **Color pairing:** Soft Gradients, Luxury Facade palettes.
- **Install:** `npx shadcn@latest add @react-bits/Aurora-TS-TW`

### Particles / Orbs (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/backgrounds/particles) — MIT
- **What it is:** Floating particles or glowing orbs on a dark background.
- **Best for:** Tech, AI products, futuristic interfaces, dark UI hero sections.
- **Avoid when:** Light UI or text-heavy layouts where particles create noise.
- **Color pairing:** Otherworldly or Corporate/Enterprise palettes.
- **Install:** `npx shadcn@latest add @react-bits/Particles-TS-TW`

### Hyperspeed (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/backgrounds/hyperspeed) — MIT
- **What it is:** Star-warp / tunnel speed effect. High intensity, cinematic.
- **Best for:** Gaming, esports, launch pages, dramatic product reveals.
- **Avoid when:** Any context requiring sustained readability — this is a moment, not a surface.
- **Color pairing:** Gaming/Esports or Acid Contemporary palettes.
- **Install:** `npx shadcn@latest add @react-bits/Hyperspeed-TS-TW`

### Dot Matrix / Grid (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/backgrounds/dot-grid) — MIT
- **What it is:** Subtle animated dot or grid pattern. Minimal, structural.
- **Best for:** SaaS, developer tools, documentation sites, corporate digital.
- **Avoid when:** Organic, warm, or luxury contexts where geometric patterns feel cold.
- **Color pairing:** Minimalist or Corporate/Enterprise palettes.
- **Install:** `npx shadcn@latest add @react-bits/DotGrid-TS-TW`

### Waves (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/backgrounds/waves) — MIT
- **What it is:** Animated SVG or canvas wave pattern. Smooth, flowing.
- **Best for:** Wellness, fintech, clean SaaS section dividers, tropical/resort.
- **Avoid when:** Heavy animation budgets are already used elsewhere.
- **Color pairing:** Soft Gradients, Warm Tropical/Resort, Healthcare palettes.
- **Install:** `npx shadcn@latest add @react-bits/Waves-TS-TW`

---

## Text Animations

Use for headlines, hero text, and key callouts. Text animation draws the eye — use it on one or two elements per view, never on body copy.

> **Agent rule:** Never animate body copy or long-form text. Animation is for headlines, stats, and single-line callouts only.

### BlurText (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/text-animations/blur-text) — MIT
- **What it is:** Text fades and unblurs into focus word by word or character by character.
- **Best for:** Hero headlines, taglines, premium product reveals.
- **Avoid when:** Text needs to be instantly readable (CTAs, navigation, error messages).
- **Install:** `npx shadcn@latest add @react-bits/BlurText-TS-TW`

```tsx
import { BlurText } from './BlurText'

<BlurText
  text="Design that speaks."
  delay={150}
  animateBy="words"
  direction="top"
  className="text-5xl font-bold text-white"
/>
```

### SplitText (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/text-animations/split-text) — MIT
- **What it is:** Text splits into characters or words and animates in with spring physics.
- **Best for:** Bold editorial headlines, brand moments, dramatic reveals.
- **Avoid when:** Subtlety is required — this is a statement effect.
- **Install:** `npx shadcn@latest add @react-bits/SplitText-TS-TW`

### ShinyText (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/text-animations/shiny-text) — MIT
- **What it is:** Animated shine sweep across text. Lightweight CSS animation.
- **Best for:** Badges, labels, "New" tags, premium product callouts.
- **Avoid when:** Dark minimalist contexts where shine feels garish.
- **Install:** `npx shadcn@latest add @react-bits/ShinyText-TS-TW`

### GradientText (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/text-animations/gradient-text) — MIT
- **What it is:** Animated gradient fill on text, flowing color shift.
- **Best for:** AI product headlines, tech branding, premium SaaS hero text.
- **Avoid when:** Solid, high-contrast text is needed for accessibility.
- **Color pairing:** Use stops from Otherworldly or Soft Gradients palettes.
- **Install:** `npx shadcn@latest add @react-bits/GradientText-TS-TW`

### CountUp (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/text-animations/count-up) — MIT
- **What it is:** Animated number counter, scroll-triggered.
- **Best for:** Stats sections, metrics, social proof numbers.
- **Avoid when:** Numbers change frequently (use live data display instead).
- **Install:** `npx shadcn@latest add @react-bits/CountUp-TS-TW`

### RotatingText (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/text-animations/rotating-text) — MIT
- **What it is:** Cycles through a list of words in a single text slot. Smooth transition.
- **Best for:** Hero taglines with multiple value props ("Build faster. Ship better. Look great.").
- **Avoid when:** More than 4–5 words in the cycle — users lose track.
- **Install:** `npx shadcn@latest add @react-bits/RotatingText-TS-TW`

### TextPressure / TrueFocus (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/text-animations/true-focus) — MIT
- **What it is:** Interactive text that reacts to cursor proximity — blur/focus or pressure effect.
- **Best for:** Portfolio hero sections, interactive brand moments, creative agency pages.
- **Avoid when:** Mobile-first contexts (cursor effects don't translate).
- **Install:** `npx shadcn@latest add @react-bits/TrueFocus-TS-TW`

---

## Motion & Scroll

Scroll-triggered animations and transitions. These should feel natural, not theatrical — they guide attention rather than demand it.

> **Agent rule:** Scroll animations should have short durations (200–400ms) and use ease-out curves. Never block content visibility — always animate from visible-enough to fully visible.

### ScrollReveal (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/animations/scroll-reveal) — MIT
- **What it is:** Elements fade and slide into view as they enter the viewport.
- **Best for:** Content sections, feature grids, testimonials, any below-fold content.
- **Avoid when:** The page is short enough that everything is visible on load.
- **Install:** `npx shadcn@latest add @react-bits/ScrollReveal-TS-TW`

### FadeContent (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/animations/fade-content) — MIT
- **What it is:** Simple opacity fade-in on scroll entry. Minimal and clean.
- **Best for:** Editorial content, long-form pages, documentation.
- **Install:** `npx shadcn@latest add @react-bits/FadeContent-TS-TW`

### GlitchText (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/text-animations/glitch) — MIT
- **What it is:** Glitch/distortion effect on text. Cyberpunk aesthetic.
- **Best for:** Gaming, esports, hacker aesthetic, alt-culture brands.
- **Avoid when:** Any professional, wellness, or corporate context.
- **Color pairing:** Otherworldly, Acid Contemporary, Gaming/Esports palettes.
- **Install:** `npx shadcn@latest add @react-bits/GlitchText-TS-TW`

---

## UI Components

Interactive components with built-in motion. Use to add depth and tactility to interfaces without building custom animation logic.

### SpotlightCard (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/components/spotlight-card) — MIT
- **What it is:** Card with a radial spotlight that follows the cursor. Subtle, premium feel.
- **Best for:** Feature cards, pricing tiers, product highlights.
- **Color pairing:** Works best with dark cards — Corporate/Enterprise, Gothic, Gaming palettes.
- **Install:** `npx shadcn@latest add @react-bits/SpotlightCard-TS-TW`

### TiltCard (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/components/tilt) — MIT
- **What it is:** Card tilts in 3D perspective on hover. Parallax depth feel.
- **Best for:** Product cards, portfolio items, NFT/collectible displays.
- **Avoid when:** Accessibility is a priority — can cause motion sickness for some users. Respect `prefers-reduced-motion`.
- **Install:** `npx shadcn@latest add @react-bits/Tilt-TS-TW`

### Magnet (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/components/magnet) — MIT
- **What it is:** Element magnetically attracts toward the cursor within a radius.
- **Best for:** CTAs, social links, playful interactive moments.
- **Avoid when:** Mobile-only contexts.
- **Install:** `npx shadcn@latest add @react-bits/Magnet-TS-TW`

### PixelCard (ReactBits)
- **Source:** [ReactBits](https://reactbits.dev/components/pixel-card) — MIT
- **What it is:** Card that reveals a pixel-scatter animation on hover.
- **Best for:** Gaming, retro/pixel aesthetic, creative portfolios.
- **Color pairing:** Retro/Vintage or Gaming/Esports palettes.
- **Install:** `npx shadcn@latest add @react-bits/PixelCard-TS-TW`

### GlassCard (manual)
- **What it is:** Glassmorphism card using CSS `backdrop-filter`.
- **Best for:** Overlays on photo or gradient backgrounds, premium UI, Apple-style interfaces.
- **Avoid when:** Background is flat or plain — glass needs something behind it to work.

```css
.glass-card {
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(20px) saturate(180%);
  -webkit-backdrop-filter: blur(20px) saturate(180%);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 16px;
}
```

---

## Liquid & Glass FX

High-impact organic effects. These are statement moments — use them once per project, with intention.

> **Agent rule:** Liquid and glass effects are brand moments, not layout patterns. One use per project maximum.

### liquid-logo (paper-design)
- **Source:** [liquid-logo](https://github.com/paper-design/liquid-logo) — MIT
- **What it is:** Animated liquid morphing effect applied to a logo or SVG path. The shape breathes and flows organically.
- **Best for:** Hero logo reveals, brand identity animations, premium product launches.
- **Avoid when:** The logo needs to stay static and recognizable at all times (e.g. in a nav bar).
- **Color pairing:** Luxury, Gothic/Dark Romance, or Soft Gradients palettes work best with fluid organic motion.

```tsx
import { LiquidLogo } from '@paper-design/liquid-logo'
// install: npm i @paper-design/liquid-logo

<LiquidLogo
  src="/logo.svg"
  speed={0.8}
  color="#D4AF37"  // Golden Obsession accent
/>
```

### liquid-glass-js (dashersw)
- **Source:** [liquid-glass-js](https://github.com/dashersw/liquid-glass-js) — MIT
- **What it is:** Apple visionOS-inspired liquid glass morphing effect. Applies a distortion + refraction shader to any DOM element.
- **Best for:** Premium hero UI elements, modal overlays, product launch pages targeting Apple ecosystem audiences.
- **Avoid when:** Performance budget is tight, or the brand is not in the premium/Apple-adjacent space.
- **Color pairing:** Works best on top of rich photo or gradient backgrounds — use Luxury or Soft Gradients palettes for the background layer.

```tsx
import { LiquidGlass } from 'liquid-glass-js'
// install: npm i liquid-glass-js

<LiquidGlass>
  <div className="p-8">
    <h2>Premium feature</h2>
  </div>
</LiquidGlass>
```

---

## Shader Gradients (Advanced)

For when a static gradient is not enough. ShaderGradient renders a living, breathing gradient via WebGL — it reacts to time, mouse, and scroll.

### Key props guide

| Prop | What it controls | Recommended range |
|---|---|---|
| `uSpeed` | Animation speed | 0.1 (slow, meditative) → 0.8 (energetic) |
| `uStrength` | Distortion intensity | 1 (subtle) → 5 (dramatic) |
| `uDensity` | Wave frequency | 0.8 (wide waves) → 2.5 (tight, complex) |
| `type` | Shape | `plane` (flat), `sphere` (orb), `waterPlane` (flowing) |
| `grain` | Film grain overlay | `on` for premium feel, `off` for clean digital |
| `lightType` | Lighting model | `3d` (depth), `env` (environmental) |

### Palette recipes for ShaderGradient

| color-combo-skill palette | color1 | color2 | color3 | Mood |
|---|---|---|---|---|
| Dreamy Periwinkle | `#B8C0FF` | `#E7D8FF` | `#2D4275` | Soft, digital-premium |
| Golden Obsession | `#D4AF37` | `#1C1A17` | `#B87333` | Opulent, dark luxury |
| Neon Abyss | `#3C1A47` | `#B6FF00` | `#1A0828` | Electric, surreal |
| Midnight Frag | `#00E5FF` | `#0A0C10` | `#1A1E28` | Gaming, high-focus |
| Clinical Clarity | `#D0E8F0` | `#F7FAFB` | `#0A7A8A` | Clean, medical |
| Aurora (custom) | `#A7C4A0` | `#F4EFE6` | `#4E6B45` | Organic, wellness |

---

## 3D in UI

Use react-three-fiber when the visual goal cannot be achieved with CSS or canvas 2D. 3D adds genuine depth and interactivity — but it comes with a real performance and bundle cost.

> **Agent rule:** Only suggest R3F when the brief explicitly requires 3D depth, a product viewer, or a 3D abstract hero. Never default to R3F when a CSS gradient or ShaderGradient would do the job.

### react-three-fiber
- **Source:** [react-three-fiber](https://github.com/pmndrs/react-three-fiber) — MIT
- **What it is:** React renderer for Three.js. Write 3D scenes as JSX components with full React state/hooks integration.
- **Best for:** 3D product viewers, abstract animated 3D hero sections, particle systems with physics, interactive data visualizations.
- **Avoid when:** The effect can be achieved with ShaderGradient, CSS, or canvas 2D — those are significantly lighter.
- **Bundle note:** Three.js is ~600KB. Always code-split and lazy-load the 3D canvas.

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
        <MeshDistortMaterial
          color="#4B2E83"  // Futuristic Elegance accent
          distort={0.4}
          speed={1.5}
          roughness={0.2}
        />
      </mesh>
      <OrbitControls enableZoom={false} autoRotate />
    </Canvas>
  )
}
```

---

## Performance Tiers

Always match effect weight to context. Use this as a quick check before recommending any effect.

| Tier | Effects | When to use |
|---|---|---|
| **Lightweight** | CSS gradient animation, ShinyText, CountUp, FadeContent, DotGrid | Any project, including mobile-first |
| **Medium** | Aurora, Waves, BlurText, SplitText, SpotlightCard, ShaderGradient | Projects with controlled bundle size and modern device targets |
| **Heavy** | Ballpit, Hyperspeed, Particles, liquid-glass-js, TiltCard | Landing pages, portfolio, launch pages — not SaaS product UI |
| **Maximum** | react-three-fiber, liquid-logo with complex SVG | Hero-only, code-split, with static fallback mandatory |

---

## Accessibility Rules

- **Always respect `prefers-reduced-motion`.** Wrap animated components in a check and fall back to static content.
- **Never animate body text** — only headlines, decorative elements, and UI micro-interactions.
- **Contrast still applies.** Animated text must still pass WCAG contrast at every frame, not just at rest.
- **Don't rely on motion to convey meaning** — if the animation is removed, the content must still make sense.

```tsx
const prefersReducedMotion =
  window.matchMedia('(prefers-reduced-motion: reduce)').matches

// Then conditionally render the animated vs static version
{prefersReducedMotion ? <h1>{text}</h1> : <BlurText text={text} />}
```

---

## Color Bridge

This skill works in tandem with [color-combo-skill](https://github.com/bilioveloso/color-combo-skill). When applying any effect, always source colors from a named palette rather than picking arbitrary hex values.

| Effect context | Recommended palette category |
|---|---|
| AI/tech SaaS hero with ShaderGradient | Otherworldly or Soft Gradients |
| Dark gaming hero with Hyperspeed or Particles | Gaming / Esports |
| Premium brand hero with liquid-logo | Luxury |
| Wellness app with Aurora or Waves | Soft Gradients or Nature / Organic |
| Corporate dashboard with DotGrid | Corporate / Enterprise |
| Gothic editorial with shader or glass | Gothic / Dark Romance |
| Playful consumer with Ballpit | Acid Contemporary or Warm Tropical / Resort |
