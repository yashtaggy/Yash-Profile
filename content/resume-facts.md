# Resume facts: single source of truth for the portfolio

Rules: use only what is written here. Missing items are marked TODO(content). Items marked CONFIRM are believed correct but need the owner's check before launch.

## Identity
- Public name: Yash Tagunde. Alternate name (structured data only): Yash Bharat Tagunde.
- Base location (show in hero): Pune, India. Do not add relocation wording.
- Email for the site: yashtaggy1603@gmail.com
- LinkedIn: https://www.linkedin.com/in/yash-t-a4330b1b5/
- GitHub: https://github.com/yashtaggy
- Phone: exists on the resume, but DO NOT display it on the site.

## Positioning
- Hero headline: "I build AI agents that do real work."
- Hero sub-line: "AI engineer and software engineer. Top 10 at the Capgemini Exceller AgentifAI Buildathon 2026 Grand Finale. Rank winner, Google Cloud GenAI Exchange Hackathon 2025."
- Small line: "B.Tech, Computer Science & Engineering (AI & Edge Computing), MIT ADT University. Based in Pune, India."
- Proof chips: Top 10, Capgemini Exceller AgentifAI Buildathon 2026 Grand Finale | Rank winner, Google Cloud GenAI Exchange Hackathon 2025 (CONFIRM exact event name) | AWS Certified AI Practitioner and Cloud Practitioner
- Proof strip numbers (only these): 5-member team led (Orion) | 2 AWS certifications | 500+ children reached through Bhumi Foundation | 8.18/10 CGPA
- Summary (from the resume): Computer Science Engineer specializing in Artificial Intelligence, with hands-on experience at the intersection of AI, business, and enterprise technology. Experienced in building GenAI applications and AI-driven automation while translating business requirements into technology solutions through presales and opportunity intelligence initiatives. Team Captain at the Capgemini Exceller AgentifAI Buildathon 2026 Grand Finale and Rank Winner at the Google Cloud GenAI Exchange Hackathon 2025. AWS Certified in Cloud and AI, with a strong interest in AI strategy, digital transformation, and data-driven business solutions. DELF B2 certified French language speaker.

## Education
- MIT Art, Design & Technology University, Pune. B.Tech, Computer Science & Engineering (Artificial Intelligence & Edge Computing). Aug 2022 to May 2026. CGPA 8.18/10.

## Experience (show in the timeline at resume level only)
### LTM (LTIMindtree), Business Analyst Intern, Pune, Feb 2026 to Aug 2026
- Developed AI agents using Microsoft Copilot Studio and Power Automate to automate enterprise presales workflows.
- Built AI-powered opportunity intelligence workflows by mining enterprise datasets and collaborating with Delivery Managers and Solution Architects to identify high-value business opportunities.
- Conducted business analysis to support a go-to-market strategy with a technology partner, and developed a strategy deck with a roadmap towards a business target.
- Restrictions: no client or partner internal figures, no screenshots, no workflow diagrams, no case study. Keep to this wording level. (Owner has not confirmed permission to publish LTM work.)

### SETV Global, Product Developer Intern, Remote, Sep 2025 to Dec 2025
- Developed cloud-native MedTech AI solutions using Python, Azure, Docker and Infrastructure as Code.
- Automated deployment workflows and created technical documentation while collaborating with cross-functional teams on AI-driven healthcare solutions.
- Restrictions: no patient data, no company-confidential details.

## Projects
### Orion: API intelligence platform (June 2026)
- Result: Top 10, Capgemini Exceller AgentifAI Buildathon 2026 Grand Finale. Role: Team Captain, led a 5-member team.
- Live: https://agentif-ai.vercel.app/ | Code: https://github.com/yashtaggy/AgentifAI
- What it does: paste an OpenAPI or Swagger URL and get a full developer explorer, live API calls, API diffs and automated security audits. The resume describes it as an agentic AI platform for API migration, security auditing and SDK generation.
- Modes visible in the live app: Explorer Mode, Intent Mode, API Diff, Security Audit; also Generate SDK, an API playground with session chain variables, and an AI Assistant for code, auth and cURL help.
- Sample specs offered in the app: Petstore, Spotify, Kubernetes, OpenAI.
- Stack: Next.js, React, TypeScript, Tailwind CSS, Monaco editor, Next.js API routes, Groq API with LLaMA 3.3 70B.
- Data flow (from the README): URL, server-side proxy fetch, OpenAPI parser, normalized API model, then Explorer, Playground and the AI Assistant (given structured API context) producing explanations, code and debugging help.
- Reliability work: a custom `safeParseJSON` utility for robust parsing of LLM output (CONFIRM where it lives in the repo and what it handles). Validated through real-world API test cases (TODO(content): how many APIs, what failed before).
- Needed assets: TODO(content): 4 to 6 screenshots, 60 to 90 second demo video, architecture diagram.

### ArtifyAI: AI-powered marketplace assistant for artisans (Jul 2025 to Nov 2025)
- Result: Rank winner, Google Cloud GenAI Exchange Hackathon 2025 (CONFIRM exact name: the repo README says H2Skilles Gen AI Exchange Hackathon 2025).
- Code: https://github.com/yashtaggy/Artify-AI
- What it does: helps local artisans market their crafts, tell authentic stories, understand demand and reach wider audiences.
- Features (from the README): Story Generator with a Provenance Card (Gemini Flash 2.5), Trend Finder, Craft Score for cost, price range and sustainability (Cohere Command R+), Market Demand Analysis, Ad Creatives Generator, My Library for saved outputs. (CONFIRM which features the owner built.)
- Stack: Next.js, Tailwind CSS, Firebase Authentication, Firestore and Cloud Storage, Gemini Flash 2.5, Cohere Command R+, Chart.js, D3.js, Google Cloud Platform.
- NEVER state any percentage for digital reach. That figure is unverified.
- Needed assets: TODO(content): screenshots or demo-video frames; the README links a live app, a demo video and a blog post.

### Shreyash Solutions website (company website, live)
- Link: https://shreyashsolutions.com/
- What it is: a complete website the owner built for his parents' company, Shreyash Solutions, a Pune-based manufacturer of precision potentiometric sensors and electromechanical assemblies. It has a working contact-us backend and SEO enabled; the owner reports it ranks first on Google for the company name (CONFIRM in a private window before stating it).
- Tech stack: TODO(content). Looks like Next.js (CONFIRM). Contact backend: TODO(content). SEO work done: TODO(content).
- Needed assets: TODO(content): desktop and mobile screenshots.
- Before featuring: the owner should check inconsistent text on the live site (the linearity figure appears with different values in different places).

## Skills (group by outcome on the site)
- Build agents and AI products: Agentic AI, LangChain, LLMs, RAG, Generative AI, Machine Learning, Deep Learning, Microsoft Copilot Studio, Power Automate
- Ship software: Python, Java, TypeScript, SQL, OOP, Data Structures & Algorithms, Next.js, Git/GitHub
- Cloud and DevOps: AWS, GCP, Azure, Docker, CI/CD, Jenkins, Infrastructure as Code
- Analyse and present: Microsoft Excel, PowerPoint, Power BI

## Certifications
- AWS Certified AI Practitioner (Amazon Web Services)
- AWS Certified Cloud Practitioner (Amazon Web Services)
- DELF B2, France Education international
- TODO(content): credential links or badge IDs

## Leadership and community
- Project Lead and Volunteer, Bhumi Foundation, 2024 to present. Led weekly educational programs across multiple centres, coordinating and mentoring volunteer teams to deliver structured learning for underprivileged children. Planned and executed community initiatives spanning education, fundraising, donation drives and civic engagement, reaching 500+ children.
- Never publish photos of children.

## Languages
- English (Professional), French (DELF B2), Hindi (Native), Marathi (Native)

## Photos (owner supplies; file names to use in public/images)
- headshot-primary.jpg (hero, share image), headshot-casual.jpg (About)
- capgemini-agentifai-2026-solo.jpg, capgemini-agentifai-2026-team.jpg
- google-genai-exchange-2025-solo.jpg, google-genai-exchange-2025-team.jpg
- Until they exist, render tasteful gradient placeholders, not stock photos.

## Notes blog (starter post ideas)
- How I made LLM JSON output reliable in Orion
- How I got a company website to rank first on Google (only after the ranking is confirmed)
