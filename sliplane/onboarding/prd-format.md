# PRD output format

Every PRD you publish uses this exact structure. Brevity is a feature.

```markdown
# <one-line title that names the thing>

**Loop:** tech | business
**Date:** YYYY-MM-DD
**Confidence:** high | medium | low
**Reframed gate:** <which calendar gate or 'North Star'>

## What

One paragraph. State the finding/opportunity/threat in plain language. Lead with the substance, not background. If you're proposing something to build, state what it is in one sentence, then why it matters in 2-3 sentences.

## Evidence

3-7 bullets, each with a source link. Quote verbatim where it carries weight. Date every source.

- [Source name + date](url) — quote or specific fact
- [...]

## Why now

2-3 sentences. What changed in the world that makes this matter THIS WEEK, not next quarter? If you can't answer this, the PRD probably doesn't pass the build-bar.

## Build sketch (if proposing a build)

- 3-6 concrete steps
- File paths where obvious: `packages/reframed-cli/src/...`
- Sub-agent dispatch suggestion: which kind of agent (Claude Code / Codex / sub-bot), how many in parallel
- Rough scope: hours / days / weeks
- Test path: how would Alex know this is working

## Cost / risk

- Token cost estimate if relevant
- Sovereignty implication (does this cross the cognitive-data boundary? If yes, flag and recommend local-only path)
- Customer-facing implication (is this load-bearing for voice fidelity, anti-fabrication, or the discreet-job-hunter positioning?)
- Failure modes — what could go wrong, what's the cleanup

## Decision needed from Alex

One sentence. What's the specific ask?

- "Build now / build later / don't build"
- "Reach out to this person / don't"
- "Update landing copy / don't"
- "Pivot Tier 1 pricing / hold"

## Sources

Full link list (different from Evidence inline links — this is the complete source bibliography).
```

## Status updates (when nothing passes the bar)

Path: `/proposals/status/YYYY-MM-DD-{loop}.md`

```markdown
# {tech|business} loop status — YYYY-MM-DD

Nothing crossed the build-bar today.

Scanned: <list sources, ~5 bullets>
Watched: <list signals you're tracking but not yet acting on, ~3 bullets>
Next check: <next cron tick>
```

These are short. ~10 lines max. They prevent Alex from worrying he missed something while keeping the PRD signal-to-noise high.

## Naming

- PRDs: `proposals/{tech|business}/YYYY-MM-DD-<short-slug>.md`
- Slug: 3-6 words, lowercase, hyphenated, descriptive
- Examples:
  - `2026-05-12-jobright-cli-launch-rumor.md`
  - `2026-05-12-smolagents-code-action-adopt.md`
  - `2026-05-12-discreet-reddit-leads-may.md`
