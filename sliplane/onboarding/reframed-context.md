# Reframed — context for the researcher

## What Reframed is

Reframed is a voice-fidelity resume-tailoring product. The tailoring engine takes a user's master resume + a job listing URL and produces a tailored resume + cover letter that sounds like the user wrote it, not like ChatGPT did.

The differentiation against JobRight / Teal / Jobscan is **architectural, not aesthetic**:
- **Voice fingerprinting**: derives a per-user voice profile from the master resume and any external inputs (LinkedIn, GitHub, Substack, personal site). Tailored output must pass voice-check rules before export.
- **Anti-fabrication**: factual claims are grounded in the master corpus only. The engine refuses to invent credentials, dates, or accomplishments. Confidence flags surface when JD signals invite stretch.
- **Cognitive culture matching**: scrapes public signals about company culture (context-switching load, focus depth) and surfaces them as ranking factors, not prescriptive vetoes. Grounded in independently published triple-network coupling research (GL-001 preprint, Guardian Labs / TRIM).

## The wedge

**The Discreet Job Hunt for senior ICs** — engineers/leads at stable companies quietly testing the market. Aversion to LinkedIn theater is the customer fit, not a side feature. They want CLI because dashboards leave audit trails. They want voice fidelity because hiding the job hunt. They want batch tailoring for stealth scale (50 résumés over a month, not a spike).

## Three-tier pricing (locked 2026-04-28)

- **Tier 1 Solo**: $50/mo flat with soft fair-use cap. CLI-first integration for AI-native job seekers. **The headless GTM wedge.**
- **Tier 2 Recruiter**: $500-$2K/mo. Multi-candidate dashboard, recruiter analytics. Opens at $5K MRR.
- **Tier 3 Enterprise**: $50K-$150K white-label/acquihire. Cognitive phenotype matching becomes embedded infrastructure.

## The Jun 9 North Star

**10 paying Tier 1 customers ($500 MRR) AND ≥5 of them with real interviews from Reframed-tailored applications, by 2026-06-09.** MRR alone is vanity if churn is high — interview-conversion is the durable signal.

Floor scenario: 8 weeks (~2026-06-23) if USPTO + branding + Adzuna polish slip.

## V2 in-scope features (locked)

- **Headless CLI** — primary Tier 1 surface (`reframed tailor <job-url> < resume.md`)
- **Browser extension** — secondary surface; drops "Tailor with Reframed" button onto LinkedIn / Indeed / Greenhouse / Ashby / Lever job pages
- **External-facing profile upload** — LinkedIn + GitHub + Substack + personal site + ORCID + X handles → richer voice fingerprint
- **Resume design picker** — 3-4 curated templates (modern-clean / classic-serif / tech-monospace / executive-clean)
- **A2A endpoint** at `reframed.works/.well-known/a2a-agent-card.json`
- **Per-user constitutionMd substrate** — each user's voice + preferences as a constitutional document
- **Command bar UX** — Cmd+K, Linear/Arc pattern
- **Bullet library + known-errors auto-correction + "should I apply" pre-report + story bank**
- **Archetype emergence from usage** — clusters from accumulated tailor history (NOT predefined modes)

## Competitive set (May 2026)

| Player | Position |
|---|---|
| **JobRight** | Full copilot, 8M+ listings, "90% auto-apply." Reddit complaints: keyword stuffing, hallucinated credentials. Primary competitor — their failures sell Reframed's story. |
| **Teal** | Tailoring + tracker. Polished UX. Mid-threat. |
| **FinalRound AI** | Interview prep — different lane, potential partner. |
| **Kickresume / Rezi / Jobscan / Reztune / ResumeHog** | Legacy + micro-tools. Long-tail. |

**Headless CLI for AI-native users: literally no one ships it as of May 2026.** Wedge is unfilled.

## New regime to watch — "Automation Fingerprinting"

LinkedIn, Indeed, and specialized tech boards now detect AI-submitted applications by measuring zero "human-like dwell time" + lack of hyper-specific customization, flagging them as spam. **Reframed's voice fidelity + factual customization is the only AI tool architected to pass this.** Position this in landing copy and outreach.

## What you're looking for

Your job is to surface anything that:
- Materially advances Reframed toward Jun 9 (acquisition leads, retention insights, conversion patterns)
- Threatens Reframed's wedge (competitor launches, new ATS-side defenses, pricing pressure)
- Strengthens the moat (anti-fabrication research, voice-fingerprinting papers, cognitive matching research)
- Opens new positioning angles (frames Alex hasn't articulated yet)
- Sources customers (discreet-job-hunter mentions in the wild — these are gold)

## What you should ignore

- Generic AI news without Reframed implications
- Frontier-lab benchmark wars (interesting but not actionable for a solo founder pre-revenue)
- Anything that requires "we should add another platform" without a clear customer signal
- Cognitive/clinical/TRIM/Guardian-tagged content (sovereignty boundary)
