# Business loop — every 6h, offset 3h from tech loop

## Your mission this cycle

Scan for anything that:
- Moves Reframed toward **Jun 9 North Star** (acquisition leads, retention insights, conversion patterns)
- Threatens Reframed's **wedge** (competitor launches, ATS-side defenses, pricing pressure, narrative shifts)
- Sources **discreet-job-hunter customers** in the wild — these are gold
- Opens new **positioning angles** Alex hasn't articulated yet

## Sources to scan (in priority order)

1. **Reddit** — these subs first:
   - r/cscareerquestions (largest pool of senior ICs in market-testing mode)
   - r/cscareers
   - r/recruitinghell (frustrations with current AI tools = opportunity)
   - r/ExperiencedDevs
   - r/jobs (broader signal)
   - Recent posts/comments only — last 24-48h

2. **X / Twitter** — relevant accounts and search terms:
   - Accounts: agentic-coding influencers (agentic.james, Karpathy, ekzhang, jxmnop, swyx, simonw)
   - Searches: "resume AI" "tailor resume" "job search AI" "ATS hack" "looking for a resume tool"
   - Filter for engagement (>10 likes) to avoid noise

3. **HN** — Show HN, Ask HN, Launch HN posts in last 7 days touching career/resume/agentic-coding

4. **Product Hunt** — daily launches filtered for career/hiring/AI-resume categories

5. **Competitor changelogs / blogs** (last 7 days):
   - jobright.ai/blog
   - tealhq.com/blog
   - finalroundai.com/blog
   - Any new launches from Kickresume, Rezi, Jobscan, Reztune, ResumeHog

6. **AI-native SaaS pricing patterns** — note any new headless-CLI tools, new $-tier patterns ($50/mo, $200/mo, etc.), new "passes ATS detection" claims

## Specific signal types to flag

### Acquisition leads (highest priority)

Anyone publicly looking for **what Reframed already does**:
- "Looking for a resume tool that doesn't sound like ChatGPT"
- "Want AI tailoring without keyword stuffing"
- "Need a CLI / API for resume work" (rare — when found, immediate flag)
- "Tired of LinkedIn-easy-apply spam"
- "Discreet job search" / "stealth job hunt" mentions

For each: capture username, post URL, post date, what they're looking for, their context (job title if visible, technical level). Alex DMs personally — these are not for automation.

### Competitor moves

- New features launched by JobRight / Teal / FinalRound
- Pricing changes
- Public reviews (positive or negative — both inform positioning)
- Marketing copy shifts (what they're claiming this month)
- Funding events / acquisitions

### Threats

- New ATS-side AI-detection regimes
- New job boards or hiring platforms with built-in AI tailoring
- Discounting pressure from competitors
- Public claims that overlap with Reframed's positioning (especially "voice fidelity," "anti-fabrication," "non-keyword-stuffing")

### Positioning angles

- New framings the market is using ("automation fingerprinting" was last week's example)
- Memes / cultural shifts in how senior ICs talk about job searching
- Adjacent products that could be partner targets

## What to do with findings

- **Acquisition leads** → always write a PRD (these are time-sensitive). Format:
  - One-paragraph "What" with username + post + their context
  - "Why now" = why they're a fit + why 48h matters
  - Build sketch = N/A (this is a Decision: "DM personally")
  - Decision needed = "Alex DM this person in next 48h?"
- **Competitor moves / threats / angles** → PRD if material, status note if minor

At end of cycle:
- `git commit` + `git push origin main` (GitHub is the sole publish surface in v1)

## Honest stop conditions

- 20 min max per cycle.
- Acquisition lead found → priority commit (prefix subject with 🎯 emoji so it stands out on GitHub).
- If today's competitor-blog scan shows nothing new from any of the top 5, that's fine — note it.
- If you find an acquisition lead but their post is >48h old and unresponded, lower priority but still surface.

## Remember

Customer acquisition is the bottleneck for Jun 9. **You finding one real lead per week pays back your entire annual cost.** Take this seriously.
