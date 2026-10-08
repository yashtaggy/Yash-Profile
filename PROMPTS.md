# Portfolio build kit: setup and prompt sequence for Antigravity

How it works: three files (AGENTS.md, a design rule, a QA skill) teach the agent your project once, so each prompt below can be short. You run the prompts in order, one per conversation, check the result in the browser, then commit.

## Part A: one-time setup (about 30 minutes)

1. Install Node.js (current LTS), Git and pnpm (`npm install -g pnpm`). Install Antigravity from antigravity.google and sign in with your Google account (free Individual plan).
2. On GitHub, create an empty repository named `portfolio`. Clone it to your computer.
3. Unzip this kit into the repository folder so you have `AGENTS.md`, `.agents/` and `content/` at the top level. Do not run `create-next-app` yourself; Prompt 0 does it.
4. Open the folder in Antigravity. In the Customizations panel (agent side panel, the "..." menu), check that two rules are listed (AGENTS.md and design) and that the `portfolio-qa` skill is visible. If the skill is missing, add it in the Skills tab, pointing at `.agents/skills/portfolio-qa`.
5. Add the Context7 MCP server so the agent reads current library docs instead of guessing old APIs. In the MCP servers panel, open the raw config and add:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

   Menu names change between Antigravity versions; if you cannot find it, use the Customizations panel search. Do not add more MCP servers for now: each one adds tool descriptions to the agent's context and uses your free quota. The built-in browser agent (not an MCP server) is what verifies the UI.
6. Before you use your résumé on the site: remove the "60%" claim from ArtifyAI, fix the Orion link to https://agentif-ai.vercel.app/ and the LinkedIn address, then save it as `public/resume/Yash_Tagunde_Resume.pdf` once the repo exists.
7. Photos: when ready, put them in `public/images` with the names listed at the bottom of `content/resume-facts.md`. You do not need them to start; the site shows gradient placeholders.

## Part B: how to work with the agent (free tier)

- Use Planning mode for the prompts marked PLAN (they touch many files): read the plan, fix it, then approve. Use Fast mode for small fixes.
- Free quota is weekly and metered by agent work, not prompts. Use your strongest available model for the design-heavy prompts (1, 4, 5, 7) and a faster model for 0, 2, 3, 9, 11.
- One prompt per conversation. Start a new conversation for each, and paste only the prompt. The rules and skill load automatically.
- After each prompt: look at the page yourself on your phone (the dev server address on your Wi-Fi, or the Vercel preview), then commit. If it is wrong, use the fix prompts in Part D instead of rewriting the big prompt.
- If your quota runs out mid-build, use the Handover prompt in Part D, and continue when it resets. Do not switch to a different tool mid-prompt.

## Part C: the prompt sequence

### Prompt 0: scaffold (PLAN)
```
Read AGENTS.md, .agents/rules/design.md and content/resume-facts.md. Then scaffold the project.
The folder already contains those files, so create the Next.js app in a temporary subfolder and move its files into the repo root without overwriting AGENTS.md, .agents or content.
Requirements: Next.js App Router, TypeScript strict, Tailwind CSS, ESLint, src/ directory, pnpm.
Install: motion, gsap, lenis, lucide-react, next-themes, and the MDX packages for Next.js (check the current docs for the right setup).
Create folders: src/components, src/content, src/lib, public/images, public/resume.
Add .env.example with NEXT_PUBLIC_SITE_URL, RESEND_API_KEY, CONTACT_TO_EMAIL and CONTACT_FROM_EMAIL.
Initialise git if needed and commit "chore: scaffold".
Done when `pnpm dev` starts and `pnpm build` passes. Show me the folder structure.
```

### Prompt 1: design system, fonts, themes (PLAN)
```
Implement the design system from .agents/rules/design.md.
1. CSS variables for both themes in globals.css, mapped into the Tailwind theme (colours, radii, fonts).
2. next/font for Bricolage Grotesque, Instrument Sans and JetBrains Mono.
3. Light theme by default with a dark toggle using next-themes: no flash of the wrong theme, remember the visitor's choice.
4. A grain overlay utility and a gradient-blob background component, each tuned separately for light and dark.
5. A dev-only page /styleguide showing colour tokens, the type scale, buttons (primary, secondary, ghost), tags, cards and the section heading style in both themes.
Do not build real sections yet.
Verify in the browser at 375px and 1440px in both themes and report the contrast ratio of each text and background pair.
Done when /styleguide looks like a deliberate design system, not a default template.
```

### Prompt 2: content layer
```
Convert content/resume-facts.md into typed data under src/content: profile.ts, experience.ts, projects.ts, skills.ts, credentials.ts (education, certifications, languages), recognition.ts, links.ts and lenses.ts, with types in src/content/types.ts.
Follow every rule in AGENTS.md: keep TODO(content) items as a `todo` string field instead of inventing text; leave out the phone number, the 60% claim and any LTM detail beyond the listed bullets.
lenses.ts defines the role lens order of project slugs: AI Engineer: orion, artifyai, shreyash-solutions. Software Engineer: shreyash-solutions, orion, artifyai. Agent Developer: orion, artifyai, shreyash-solutions. Analyst: artifyai, orion, shreyash-solutions.
Add a script `pnpm content:check` that lists every open TODO(content) item.
No UI yet. Done when `pnpm build` passes and content:check prints the open items.
```

### Prompt 3: site shell
```
Build the site shell: a skip link, a header with the wordmark "Yash Tagunde", nav anchors (Work, Experience, Skills, Recognition, About, Contact) with a scroll-spy active state, a Résumé button linking to /resume, the theme toggle, and an accessible mobile menu (focus trapped, closes on Escape and route change).
Add a thin scroll-progress bar, Lenis smooth scrolling (off for prefers-reduced-motion), and a footer with email, LinkedIn, GitHub and a small "Built with Next.js" line, all from src/content.
The header is translucent over content and gains a hairline border after scrolling.
Verify at 375px, 768px and 1440px and with the keyboard only. Commit when done.
```

### Prompt 4: Hero and Proof strip
```
Build the Hero and the Proof strip from src/content.
Hero: left-aligned editorial layout. The headline reveals line by line from a mask with an 80ms stagger. Include the sub-line, the three proof chips, and three buttons: View work (scrolls to Selected work), Download résumé, Email me. Add the small line that says Pune. The h1 must contain "Yash Tagunde" (an eyebrow line above the headline can sit inside the h1).
Right side: the headshot frame using public/images/headshot-primary.jpg if present, otherwise an elegant gradient placeholder with the initials YT.
Background: drifting gradient blobs and grain, tuned for both themes.
Below the fold: the Proof strip with the four numbers from content, counting up once when visible.
Under the hero buttons add the role lens control as a visual skeleton only (AI Engineer, Software Engineer, Agent Developer, Analyst; AI Engineer selected).
Mobile: stacked, headshot first, smaller type.
Verify at the three widths in both themes, then run the portfolio-qa skill.
```

### Prompt 5: Selected work and the role lens
```
Build the Selected work section with the three project cards from src/content/projects.ts.
Desktop: sticky stacking cards using GSAP ScrollTrigger. Each card pins and the next slides over it, with a subtle scale and dim on the card beneath. Each card shows the title, a one-line outcome, a result badge, tech tags in the mono font, an image area (gradient placeholder with the project name until screenshots exist), and Case study, Live and GitHub links (only those with real URLs).
Mobile and reduced motion: a normal vertical stack with no pinning.
Make the role lens functional: choosing a role re-orders the cards using the order in lenses.ts and highlights the matching tech tags, animated with Motion layout animations. Default is AI Engineer. Persist nothing.
Verify and run the portfolio-qa skill.
```

### Prompt 6: Experience, Skills, Education and certifications
```
Build three sections.
1. Experience: a vertical timeline for LTM and SETV Global using only the résumé-level bullets. The line draws as you scroll (GSAP scrub; off under reduced motion and below 768px) and each role lights up as it arrives.
2. Skills: an asymmetric bento grid with the four groups from skills.ts, tiles of different sizes, a cursor-following spotlight glow on hover (desktop only), fully keyboard accessible. No logo clouds and no percentage bars.
3. Education and certifications: a compact two-column block with the degree and CGPA, the two AWS certifications and DELF B2. Credential links marked TODO render as plain text for now.
Verify and run the portfolio-qa skill.
```

### Prompt 7: Recognition, About, Contact
```
Build Recognition, About and Contact.
Recognition: the two hackathons as large editorial entries (event, year, result, role, one sentence) with photos from public/images when they exist, gradient placeholders with captions when they do not. Desktop: a pinned horizontal gallery driven by vertical scroll. Mobile: a scroll-snap carousel with visible dots.
About: a bento layout with a short paragraph from content (a TODO(content) placeholder if none), languages, and the Bhumi Foundation volunteering. No photos of children.
Contact: a heading, email, LinkedIn, GitHub, and a form (name, email, message) with client and server validation, a hidden honeypot field and simple in-memory rate limiting. A route handler at src/app/api/contact/route.ts sends through Resend when RESEND_API_KEY is set; otherwise it logs in development only and returns success. Recipient and sender come from env vars; the recipient defaults to yashtaggy1603@gmail.com. Accessible error and success states.
Verify and run the portfolio-qa skill.
```
Resend note: on its free plan without a verified domain you can only send from the address Resend gives you to your own email. That is enough for a portfolio contact form.

### Prompt 8: case studies, résumé page, notes (PLAN)
```
Build the case-study system and the remaining routes.
1. /projects/[slug] rendered from MDX: hero (title, result badge, links, tech tags), a sticky mini table of contents on desktop, and sections: Problem, What I built and why, How it works, The hard part, Result, What I would do next.
2. Write first drafts of three case studies (orion, artifyai, shreyash-solutions) using ONLY facts in content/resume-facts.md. Where facts are missing, show a visible "Draft: add X" callout component instead of inventing anything.
3. For "How it works", draw clean inline SVG diagram components that use the design tokens and work in both themes: Orion as the data flow from the README in 6 to 7 boxes; ArtifyAI as Firebase auth, Gemini and Cohere calls, Firestore; Shreyash Solutions as a simple page map.
4. /resume: embed public/resume/Yash_Tagunde_Resume.pdf with a download button, with a graceful message if the file is missing.
5. /notes and /notes/[slug] with two starter drafts from the post ideas in resume-facts.md, marked draft: true and hidden from the index, sitemap and production until draft is false.
Verify and run the portfolio-qa skill.
```

### Prompt 9: SEO and structured data
```
Implement SEO.
Use the Metadata API: metadataBase from NEXT_PUBLIC_SITE_URL, a title template, default title "Yash Tagunde — AI Engineer & Software Engineer", a description under 155 characters naming the roles and the two hackathon results, canonical URLs, Open Graph and Twitter cards, and per-page metadata for case studies and notes.
Add Person JSON-LD on the home page: name, alternateName "Yash Bharat Tagunde", jobTitle, url, image, sameAs for LinkedIn and GitHub, alumniOf MIT Art, Design & Technology University, and a knowsAbout list. Add Article JSON-LD on published notes.
Generate app/sitemap.ts, app/robots.ts and a dynamic Open Graph image with next/og using the design tokens. Add a favicon and apple icon made from the initials.
Confirm the home page has exactly one h1 containing the name and that all content is server-rendered.
Report what you added, then run the portfolio-qa skill.
```

### Prompt 10: polish
```
Run a full polish pass on the whole site with the portfolio-qa skill.
Then: tune motion timing so no section feels sluggish; make sure all content is still visible if JavaScript animations fail; check keyboard and screen-reader flow; optimise images; load GSAP plugins only where used; aim for Lighthouse mobile 90+ in every category.
Give me the findings table, fix everything marked high, and list every TODO(content) item still open.
```

### Prompt 11: deploy preparation
```
Prepare for Vercel deployment. Confirm `pnpm build` passes. Write a README.md for the repo (what it is, stack, how to run it, how the content files work). Make sure .env.example is complete and list exactly which environment variables I must set in Vercel. Do not push anything: give me the git commands to run myself.
```

After Prompt 11 (your steps, free): push to GitHub; in Vercel choose "Add New Project", import the repo, name the project `yash-tagunde`, add the environment variables, deploy. Set NEXT_PUBLIC_SITE_URL to the final address, redeploy. Then in Google Search Console add the site as a URL-prefix property, verify with the HTML tag method, submit `/sitemap.xml` and use URL Inspection to request indexing. Add the site link to LinkedIn, GitHub and the Orion and ArtifyAI repo descriptions.

## Part D: reusable prompts

Fix loop (when something looks off)
```
Open the page in the browser at 375px and 1440px. List what is wrong (spacing, overlap, hierarchy, contrast, motion). Fix the top three issues only, then show me the result at both sizes.
```

De-template prompt (when it looks generic)
```
Act as a senior designer at a top product studio reviewing this section for a candidate's portfolio. List five specific reasons it looks templated or generic. Fix the top three while keeping the design tokens, then re-check at 375px and 1440px.
```

Copy sharpener
```
Rewrite the copy in <section> so it is specific and verb-first with no filler, shorter by a third, using only facts from content/resume-facts.md. Show before and after.
```

Wire in assets (after you add photos or screenshots)
```
I added files to public/images using the names in content/resume-facts.md. Wire them into the Hero, Recognition and project cards with next/image, responsive sizes and descriptive alt text, remove the matching placeholders, and run the portfolio-qa skill.
```

Handover (quota running out, or a conversation getting long)
```
Write HANDOFF.md at the repo root: what is finished, what is in progress, the files touched, known issues, and the exact next prompt number from PROMPTS.md. Commit it.
```

Resume in a new conversation
```
Read HANDOFF.md, AGENTS.md and the files it lists, then continue with the next step. Plan first if it touches more than three files.
```

## Part E: what to prepare while the agent builds
- Orion: 4 to 6 screenshots (landing, Explorer, Intent Mode, API Diff, Security Audit, AI Assistant) and a short screen recording. Update the repo README to match the live app and mention `safeParseJSON`.
- ArtifyAI: 4 screenshots or demo-video frames (Story Generator, Craft Score, Market Demand, My Library).
- Shreyash Solutions: desktop and mobile screenshots; confirm the stack; check the page for inconsistent figures.
- Photos: best headshot, a relaxed second photo, and the hackathon photos, named as in resume-facts.md.
- AI image prompts for backgrounds and cover art are in the blueprint doc (Photos and image prompts).
