FROM denoland/deno:bin AS deno
FROM mcr.microsoft.com/devcontainers/base:debian
COPY --from=deno /deno /usr/local/bin/deno
USER vscode
ENV OPENCODE_CONFIG=.opencode/settings.json
RUN curl -fsSL https://opencode.ai/install | bash
