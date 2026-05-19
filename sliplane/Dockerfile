FROM nousresearch/hermes-agent:latest

# Sliplane deploy — extends the official NousResearch Hermes image with our
# onboarding bundle, cli-config, and browser-harness skill. Single FROM keeps
# Sliplane's Dockerfile parser happy and cuts build time from ~10min to ~30s.

USER root

# Install browser-harness as an external skill (self-healing browser actions
# from the browser-use team; mounted via skills.external_directories in cli-config)
RUN mkdir -p /opt/hermes/skills/external && \
    git clone --depth 1 https://github.com/browser-use/browser-harness.git \
    /opt/hermes/skills/external/browser-harness && \
    chown -R hermes:hermes /opt/hermes/skills/external

# Bake the onboarding bundle and cli-config into the image (read-only at runtime)
COPY --chown=hermes:hermes sliplane/onboarding/ /opt/hermes/onboarding/
COPY --chown=hermes:hermes sliplane/cli-config.yaml /opt/hermes/cli-config.yaml

# Run as the gateway daemon — Hermes's long-running messaging-platform mode.
# Inherits ENTRYPOINT from upstream (tini → docker/entrypoint.sh).
CMD ["gateway", "run"]
