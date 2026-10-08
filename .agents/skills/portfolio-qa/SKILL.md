---
name: portfolio-qa
description: Use when finishing or reviewing any page or section of Yash's portfolio site. Runs the build, responsive, accessibility, performance, content-integrity and template-smell checks and reports findings in a table.
---

# Portfolio QA

Run these checks in order on the page or section just built. Do not declare the task done until every check passes or a failure is explained to the user.

## 1. Build health
- Run `pnpm lint` and `pnpm build`. Fix all errors and warnings you introduced.

## 2. Responsive check (browser)
Open the dev server and check each of these viewports in BOTH light and dark themes: 375x812, 768x1024, 1440x900.
- No horizontal scroll, no overlapping or clipped text, no content hidden behind fixed headers.
- Tap targets at least 44px high on mobile. Body text at least 16px.
- Images do not cause layout shift. Long words and emails wrap or truncate cleanly.

## 3. Motion check
- Animations are smooth and use only opacity and transform.
- With `prefers-reduced-motion` enabled, pinned and scrubbed effects are off and nothing important is hidden.
- Pinned and scrubbed effects are off below 768px.

## 4. Accessibility
- Keyboard: tab through the whole page. Order is logical, focus ring always visible, no keyboard traps, skip link works.
- One `h1` per page, headings in order, landmarks present, every image has alt text, buttons and links have accessible names.
- Contrast: text meets WCAG AA in both themes.

## 5. Performance
- Run a Lighthouse mobile audit if available. Targets: Performance 90+, Accessibility 95+, Best Practices 95+, SEO 95+.
- Report LCP and CLS. Heavy libraries (GSAP plugins, large images) must be loaded only where used.

## 6. Content integrity
Search the codebase and rendered text for these and fix or report each:
- The string "60%" in connection with ArtifyAI or "digital reach".
- Any LTM client name, internal figure or screenshot; any LTM case study.
- The phone number.
- "lorem ipsum", "TODO(content)" (list them all so the owner can fill them), any invented metric or testimonial.

## 7. Template-smell review
Act as a senior product designer reviewing a candidate's portfolio. List up to five specific reasons this section looks templated or generic (identical cards, centred hero, generic icons, same animation everywhere, vague copy, weak hierarchy). Fix the top three, then re-check.

## 8. Report
Finish with a short table: Check | Result | Notes. Then list what the owner must supply (photos, screenshots, copy) and what you changed.
