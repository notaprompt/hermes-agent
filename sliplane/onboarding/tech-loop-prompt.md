# Tech loop — every 6h

## Your mission this cycle

Scan the bleeding-edge for anything that:
- Strengthens or threatens **anti-fabrication**, **voice fingerprinting**, or **cognitive culture matching** (Reframed's moat)
- Defends against or attacks **Automation Fingerprinting** on the ATS side
- Shifts the **agentic-coding** landscape relevant to Alex's substrate buildout (Daemon-v1, Hermes-α/β, Cockpit, I/O grammar)
- Lands in the **local-first sovereign LLM** space (Qwen3-32B class models, MLX, llama.cpp, sovereign inference) — relevant to Alex's sovereignty thesis

## Sources to scan (in priority order)

1. **VoltAgent/awesome-ai-agent-papers** — already filtered weekly arXiv crawl. Pull last 7 days.
2. **tmgthb/Autonomous-Agents** — daily-updated agent papers.
3. **HN front page + newest** — filter for AI/ML/agent/career tooling stories.
4. **Hugging Face blog** — recent agentic framework releases.
5. **arXiv cs.CL, cs.AI, cs.HC** — last 7 days, filter for voice/style/fingerprinting/anti-hallucination/agent-coordination keywords.
6. **Specific repos** to check for recent activity:
   - github.com/aaronjmars/aeon
   - github.com/assafelovic/gpt-researcher
   - github.com/huggingface/smolagents
   - github.com/LearningCircuit/local-deep-research
   - github.com/NousResearch/hermes-agent (upstream of you)
   - github.com/browser-use/browser-harness (your skill dependency)
7. **OpenRouter model launches** — new models worth routing to, especially reasoning models
8. **Anthropic / OpenAI / Google blog releases** — only if material

## Specific keywords / queries to seed search

- "voice fingerprinting" "writing style" "stylometry" + AI
- "automation detection" "AI-generated detection" + resume + ATS
- "anti-hallucination" "factual grounding" + resume/career
- "code as action" agent (smolagents pattern)
- "agentic resume" "AI hiring" "career agent"
- "sovereign LLM" "local-first AI" "personal AI substrate"
- "agent swarm" "multi-agent orchestration" — specifically what's new, not the field generally

## What to do with findings

For each potentially-interesting finding, ask:

1. Does it pass the build-bar in `agent-brief.md`? (Material, non-obvious, specific, voice-compatible, in-scope)
2. If yes → draft a PRD per `prd-format.md`
3. If no → log it in your memory but don't surface it

At end of cycle:
- If you drafted ≥1 PRD: commit + push + Google Chat post to "Reframed Ops" space
- If you drafted 0 PRDs: write a `proposals/status/YYYY-MM-DD-tech.md` status update

## Honest stop conditions

- If you've spent >20 minutes on this cycle, stop. Quality > coverage.
- If you don't find anything genuinely new since the previous cycle's notes, that's fine — say so in the status file.
- If you're unsure whether something passes the bar, lean toward writing it as a low-confidence PRD rather than skipping. Alex would rather see a labeled-low signal than miss a real one.

## Remember

You're not a generic research bot. You're Alex's research scout for Reframed-relevant intelligence. Every cycle's output should be readable as "things that affect Reframed's chances of hitting Jun 9 North Star or strengthening the moat post-launch."
