# design-effects-skill

An agent-ready skill for design effects, animations, and visual FX.

## What this is

This repo contains a `SKILL.md` file that teaches an AI agent when and how to apply visual effects in UI and branding contexts. It covers animated backgrounds, text animations, motion patterns, liquid/glass effects, shader gradients, and 3D in UI — each with decision rules, code snippets, and guidance on when NOT to use them.

## Effect Categories

| Category | Sources |
|---|---|
| **Animated Backgrounds** | ReactBits Backgrounds + ShaderGradient |
| **Text Animations** | ReactBits Text Animations |
| **Motion & Scroll** | ReactBits Animations |
| **UI Components** | ReactBits Components |
| **Liquid & Glass FX** | liquid-logo, liquid-glass-js |
| **Shader Gradients** | @shadergradient/react |
| **3D in UI** | react-three-fiber |

## Color Integration

This skill is designed to work alongside [color-combo-skill](https://github.com/bilioveloso/color-combo-skill). Each effect section includes color pairing guidance that links back to named palettes from that skill.

## How to use

Point your agent at `SKILL.md` as a skill or context file. The agent will:

1. Use the Decision Guide to match context to an effect type.
2. Pick the named effect that fits the mood and performance budget.
3. Apply the minimal code snippet as a starting point.
4. Cross-reference color-combo-skill for palette pairing.

## Sources

- [ReactBits](https://reactbits.dev) — MIT + Commons Clause
- [ShaderGradient](https://github.com/ruucm/shadergradient) — MIT
- [liquid-logo](https://github.com/paper-design/liquid-logo) — MIT
- [liquid-glass-js](https://github.com/dashersw/liquid-glass-js) — MIT
- [react-three-fiber](https://github.com/pmndrs/react-three-fiber) — MIT

## Maintained by
[@bilioveloso](https://github.com/bilioveloso)
