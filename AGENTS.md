# Portfolio website: project brief

Owner: Yash Tagunde (public name). Alternate name: Yash Bharat Tagunde. Base: Pune, India.

## Goal
A personal portfolio site used in job applications. It must impress recruiters and hiring managers in under 30 seconds and hold up under a deeper read. Priority roles: AI Engineer and Software Development Engineer. Also: AI Agent Developer, GenAI Engineer, Data Analyst, Business Analyst.

It must look custom-designed and enterprise-grade. It must never look like a template or AI-generated site.

## Stack (no paid services)
- Next.js (App Router), TypeScript in strict mode, Tailwind CSS
- Motion (package `motion`) for component animation, GSAP + ScrollTrigger for scroll effects, Lenis for smooth scroll
- `next/font` for fonts, `next/image` for images, `lucide-react` for icons
- MDX for case studies and notes
- Package manager: pnpm
- Hosting: Vercel Hobby plan. No custom domain yet: read the site URL from `NEXT_PUBLIC_SITE_URL` (default `https://yash-tagunde.vercel.app`) so it can change later without code edits.
- Before writing code against any library, check its current docs (use the Context7 MCP server if it is available). Do not rely on memory for APIs of Next.js, Tailwind, Motion or GSAP.

## Source of truth for content
Everything about Yash comes from `content/resume-facts.md`. Rules:
- Never invent numbers, employers, awards, quotes, testimonials, client names or metrics.
- If a fact is missing, write `TODO(content): <what is needed>` in the data file and render a tasteful placeholder, never fake text.
- Do NOT use the ArtifyAI "60% digital reach" claim anywhere. It is unverified.
- Do NOT write a case study for LTM work or show any LTM client names, internal figures, screenshots or workflows. LTM appears only as the short résumé-level bullets in the Experience timeline.
- Do not display the phone number publicly. Contact is by email, LinkedIn, GitHub and the contact form.
- Keep copy specific and plain: verbs and results, no filler such as "passionate about innovation".

## Routes
- `/` single-page narrative: Hero, Proof strip, Selected work, Experience, Skills, Recognition, About, Education and certifications, Contact
- `/projects/[slug]` MDX case studies: `orion`, `artifyai`, `shreyash-solutions`
- `/notes` and `/notes/[slug]` short MDX blog
- `/resume` PDF preview and download button (file at `public/resume/Yash_Tagunde_Resume.pdf`)
- Generated: `sitemap.xml`, `robots.txt`, Open Graph image, JSON-LD

## Design
Follow `.agents/rules/design.md` exactly. Light theme is the default, dark theme is a toggle. Never use pure black or pure white.

## Engineering conventions
- Strict TypeScript, no `any`. Server components by default; add `"use client"` only for interactivity.
- Content lives in typed files under `src/content/`. Pages only render data.
- Accessible by default: semantic HTML, visible focus rings, WCAG AA contrast, alt text on every image, skip link.
- Respect `prefers-reduced-motion`: disable pinned and scrubbed effects and long animations.
- Animate only `opacity` and `transform`.
- Mobile first. Everything must work from 360px to 1920px with no horizontal scroll.
- No secrets in the repo. Use `.env.local` and keep `.env.example` current.
- Small, focused commits after each finished task, conventional style (`feat:`, `fix:`, `chore:`).

## Working protocol
1. For tasks touching more than three files, write a short plan first and wait for approval.
2. Change only what the task asks. Do not refactor unrelated files.
3. After any UI work, run the dev server, open it in the browser, check 375px, 768px and 1440px in both themes, and report what you saw.
4. Run `pnpm lint && pnpm build` before saying a task is done.
5. For a final check of a section or page, use the `portfolio-qa` skill.
6. If blocked by missing content or assets, stop and ask. Do not fill gaps with invented material.
