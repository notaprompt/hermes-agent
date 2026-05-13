# Sliplane deploy Dockerfile for the Hermes researcher (substrate-for-Reframed config)
#
# Extends the upstream Hermes image with:
#   - browser-harness (browser-use team) as an external skill
#   - Reframed-aligned onboarding bundle baked in
#   - cli-config.yaml pointing at Kimi K2.6 via OpenRouter
#   - CMD set to `gateway run` (Sliplane single-service deploy)
#
# Build from repo root with:
#   docker build -f sliplane/Dockerfile -t hermes-researcher .

FROM debian:13.4 AS base

# Reuse the upstream Dockerfile build by copying it as the actual builder.
# Sliplane points at this Dockerfile but we want all the upstream layers.
# Trick: COPY the whole context, then build via uv as upstream does.

FROM ghcr.io/astral-sh/uv:0.11.6-python3.13-trixie AS uv_source
FROM tianon/gosu:1.19-trixie AS gosu_source
FROM debian:13.4

ENV PYTHONUNBUFFERED=1
ENV PLAYWRIGHT_BROWSERS_PATH=/opt/hermes/.playwright
ENV npm_config_install_links=false
ENV HERMES_WEB_DIST=/opt/hermes/hermes_cli/web_dist
ENV HERMES_HOME=/opt/data
ENV PATH="/opt/data/.local/bin:${PATH}"

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    build-essential curl nodejs npm python3 ripgrep ffmpeg gcc python3-dev libffi-dev procps git openssh-client docker-cli tini && \
    rm -rf /var/lib/apt/lists/*

RUN useradd -u 10000 -m -d /opt/data hermes

COPY --chmod=0755 --from=gosu_source /gosu /usr/local/bin/
COPY --chmod=0755 --from=uv_source /usr/local/bin/uv /usr/local/bin/uvx /usr/local/bin/

WORKDIR /opt/hermes

# ---- Layer-cached dependency install (mirrors upstream) ----
COPY package.json package-lock.json ./
COPY web/package.json web/package-lock.json web/
COPY ui-tui/package.json ui-tui/package-lock.json ui-tui/
COPY ui-tui/packages/hermes-ink/ ui-tui/packages/hermes-ink/

RUN npm install --prefer-offline --no-audit && \
    npx playwright install --with-deps chromium --only-shell && \
    (cd web && npm install --prefer-offline --no-audit) && \
    (cd ui-tui && npm install --prefer-offline --no-audit) && \
    npm cache clean --force

COPY pyproject.toml uv.lock ./
RUN touch ./README.md
RUN uv sync --frozen --no-install-project --extra all

# ---- Source code ----
COPY --chown=hermes:hermes . .

RUN cd web && npm run build && \
    cd ../ui-tui && npm run build

USER root
RUN chmod -R a+rX /opt/hermes && \
    chown -R hermes:hermes /opt/hermes/ui-tui /opt/hermes/node_modules

RUN uv pip install --no-cache-dir --no-deps -e "."

# Google Chat dependencies (Hermes ships the integration but pubsub libs aren't in [all])
RUN uv pip install --no-cache-dir google-cloud-pubsub google-api-python-client google-auth

# ---- Sliplane-specific additions ----

# Install browser-harness as an external skill (self-healing browser actions)
RUN mkdir -p /opt/hermes/skills/external && \
    git clone --depth 1 https://github.com/browser-use/browser-harness.git /opt/hermes/skills/external/browser-harness && \
    cd /opt/hermes/skills/external/browser-harness && \
    (uv pip install --no-cache-dir -e . || pip install --break-system-packages -e . || true) && \
    chown -R hermes:hermes /opt/hermes/skills/external

# Onboarding bundle + cli-config baked into the image
# Bundle files (operational + sanitized sprint, no cognitive data per sovereignty rule)
COPY --chown=hermes:hermes sliplane/onboarding/ /opt/hermes/onboarding/
COPY --chown=hermes:hermes sliplane/cli-config.yaml /opt/hermes/cli-config.yaml

# Mount point for persistent state (Sliplane volume)
VOLUME [ "/opt/data" ]

# Sliplane runs single-service. Default to gateway daemon mode.
# To bootstrap the researcher, exec into the container post-deploy and run
# `hermes` with the agent-brief: cat /opt/hermes/onboarding/agent-brief.md | hermes
ENTRYPOINT [ "/usr/bin/tini", "-g", "--", "/opt/hermes/docker/entrypoint.sh" ]
CMD ["gateway", "run"]
