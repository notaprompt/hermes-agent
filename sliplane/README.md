# Sliplane deploy — Hermes researcher (substrate-for-Reframed)

This directory holds everything needed to deploy this hermes-agent fork as a research scout on Sliplane.

## What it does

Two scheduled Ralph-loops running every 6 hours (offset 3h):
- **Tech loop**: anti-fabrication / voice-fingerprinting / agentic-resume / sovereign-LLM intel
- **Business loop**: Reframed competitor moves, discreet-job-hunter acquisition leads, positioning intel

Each cycle drafts PRDs (if anything passes the bar), commits to `proposals/` directory, pings ntfy.

## Deploy steps

### 1. Build context

This Dockerfile (`sliplane/Dockerfile`) builds from repo root. Sliplane will clone the whole fork.

### 2. Sliplane setup

1. Sliplane dashboard → New Service
2. Connect this GitHub repo (`notaprompt/hermes-agent`)
3. Set Dockerfile path: `sliplane/Dockerfile`
4. Set build context: repo root (`.`)
5. Persistent volume: mount to `/opt/data` (Hermes home)
6. Environment variables (use Sliplane's encrypted env, not committed):
   - `OPENROUTER_API_KEY` — from `~/forge-ops/keys/sliplane-hermes-researcher` (the `openrouter:` line)
   - `GITHUB_TOKEN` — from same keyfile (`github-token:` line) — currently gh CLI token
   - `GOOGLE_CHAT_PROJECT_ID` — your GCP project ID
   - `GOOGLE_CHAT_SUBSCRIPTION_NAME` — `projects/<project-id>/subscriptions/hermes-chat-subscription`
   - `GOOGLE_CHAT_SERVICE_ACCOUNT_JSON` — `/opt/data/secrets/gchat-sa.json` (path inside container)
   - `GOOGLE_CHAT_ALLOWED_USERS` — your @reframed.works email
   - `GOOGLE_CHAT_HOME_CHANNEL_NAME` — `Reframed Ops` (must match the space name created in Google Chat)
   - `HERMES_UID=10000`, `HERMES_GID=10000` (Hermes default)
7. **Secret file mount:** upload `gchat-sa.json` to Sliplane and mount at `/opt/data/secrets/gchat-sa.json` (Sliplane has secret-file support in dashboard)
7. Resource tier: 3 vCPU / 4GB / 80GB (€9 base) — sufficient for Playwright + Chromium + Hermes

### 3. First boot

Once Sliplane shows the container as healthy:

```bash
# SSH-exec into the container via Sliplane's web terminal
hermes
# (in the hermes CLI)
> Read /opt/hermes/onboarding/agent-brief.md and follow it.
```

Hermes will:
- Read all onboarding files
- Register the two cron jobs via its `cronjob` tool
- Run one dry cycle of each loop (output to `/tmp/dry-run-{loop}.md`)
- Wait for next cron tick

### 4. Validate

After the first real cron tick (within 6h of boot):
- Check `/proposals/` in this repo on GitHub for new PRDs
- Check ntfy topic for pings
- If neither, SSH back in and inspect logs

### 5. Iterate

PRDs drop into `proposals/` for Alex's review. If patterns emerge (too many low-quality PRDs, missing a class of signals), edit the onboarding/loop files and re-deploy.

## Files in this directory

- `Dockerfile` — extends upstream Hermes image with browser-harness + onboarding bundle
- `cli-config.yaml` — Hermes config (Kimi K2.6 via OpenRouter, browser tools, skills external dir)
- `onboarding/agent-brief.md` — master prompt
- `onboarding/principles.md` — constitutional principles (sanitized)
- `onboarding/voice.md` — voice rules for PRD output
- `onboarding/reframed-context.md` — what Reframed is and why
- `onboarding/sprint-state.md` — calendar gates and current focus
- `onboarding/prd-format.md` — output format spec
- `onboarding/tech-loop-prompt.md` — what tech loop does each cycle
- `onboarding/business-loop-prompt.md` — what business loop does each cycle

## What's NOT in the bundle (sovereignty boundary)

- No cognitive memory (TRIM / Guardian / Hebbian)
- No ForgeFrame internals
- No private kid/family context
- No partner conversation details
- No specific dollar figures from runway calculations
- No active job application targets (those stay local)

This bundle is operational + sanitized sprint state. Designed to be public-safe if the fork were ever made public (it isn't required to be, but it could be).

## Killing the deploy

If this experiment doesn't earn its keep:
1. Sliplane dashboard → delete service (stops billing immediately)
2. Optional: archive the fork on GitHub
3. The local `~/forge-ops/keys/sliplane-hermes-researcher` stays — credentials reusable for future experiments
