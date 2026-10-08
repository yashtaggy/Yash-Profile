---
trigger: always_on
description: Design system for the portfolio site: colours, type, layout, motion and anti-template rules
---

# Design system: "editorial tech"

A warm, paper-toned light theme (default) and a deep indigo dark theme. One confident violet, a teal counter-accent, a saffron spark. Characterful type, generous space.

## Tokens (CSS variables on `:root` and `[data-theme="dark"]`, mapped into Tailwind theme)

| Token | Light (default) | Dark |
| --- | --- | --- |
| --bg | #F6F3EE | #0B1020 |
| --surface | #FFFFFF | #131B36 |
| --text | #14183A | #EAF0FF |
| --muted | #566086 | #9AA7C7 |
| --primary | #5B3FE0 | #7C5CFF (use #A594FF for small text) |
| --secondary | #0F9F8F | #2DD4BF |
| --spark | #D9871A | #FFB547 |
| --hairline | rgba(20,24,58,0.12) | rgba(255,255,255,0.10) |

- Never use pure black (#000) or pure white (#fff) for large areas. The light surface may be white only on cards over the paper background.
- Spark is for ONE accent per screen (a badge, a number, an underline). Do not use it for body text: contrast is too low on paper.
- Hero background: soft blurred gradient blobs in primary, secondary and a hint of spark on the base colour, plus a fine grain overlay at 3 to 4 percent opacity. Light and dark each get their own tuned version.
- Verify WCAG AA contrast for all text pairs before finishing.

## Type (load with `next/font/google`)
- Headings: Bricolage Grotesque, weight 600 to 700, tracking -0.03em, fluid size `clamp(2.75rem, 7vw, 6rem)` for the hero.
- Body: Instrument Sans, 17 to 18px, line-height 1.6.
- Labels, dates, tech tags: JetBrains Mono, small, uppercase with letter spacing, used sparingly.
- Never use Inter, Poppins, Geist or system-ui as a visible font.

## Layout
- 12-column grid, 1200px max content width, 16px side gutter on mobile.
- Section spacing: 96 to 140px on desktop, 64px on mobile.
- One card radius (20px), one pill radius (999px), one 1px hairline border style, one soft shadow style.
- Use asymmetric bento grids for skills and about, with tiles of different sizes.
- Left-aligned editorial hero. Do not centre the hero.

## Motion
- Duration 250 to 600ms, easing `cubic-bezier(0.22, 1, 0.36, 1)`.
- One signature effect per section; do not animate every element the same way:
  - Hero: line-by-line headline reveal from a mask (80ms stagger), slow drifting gradient blobs, magnetic buttons.
  - Proof strip: numbers count up once on entering the viewport.
  - Selected work: sticky stacking cards (GSAP ScrollTrigger), image tilt on hover. Role lens re-orders cards with an animated layout change.
  - Experience: a timeline line drawn by scroll scrub; each role lights up on arrival.
  - Skills: cursor-following spotlight glow inside tiles.
  - Recognition: pinned horizontal gallery on desktop, scroll-snap carousel on mobile.
  - Page changes: soft fade and slide using the View Transitions API where supported.
- Disable pinned and scrubbed effects below 768px and under `prefers-reduced-motion`.

## Anti-template rules (the site must not look vibe-coded)
- No centred hero with a gradient-text name, no waving-hand greeting, no emoji as icons.
- No grid of identical rounded cards with generic icons. Use real project imagery, diagrams and varied tile sizes.
- No glassmorphism on everything, no purple-to-blue gradient text, no default shadcn look left unstyled.
- No lorem ipsum, no placeholder stock images, no fake testimonials, no invented numbers.
- Copy is specific: what Yash built, the decision he made, the result. No filler adjectives.
- Every image has descriptive alt text. Every interactive element has a visible focus style.
