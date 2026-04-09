# Deno Dev Container Template

A TypeScript-first Deno development environment with AI-assisted coding powered by [OpenCode](https://opencode.ai).

## Features

- **Deno Runtime** — Official `denoland/deno` binary in a Debian-based dev container
- **OpenCode AI Integration** — AI pair programmer configured with MiniMax M2.7 model (pre-configured, but any OpenAI-compatible API works)
- **Deno-Native Workflow Enforcement** — Blocks Node.js/npm commands, redirects to Deno equivalents
- **Automated Code Quality Checks** — Runs `deno fmt`, `deno lint`, `deno check` automatically after edits
- **Multi-Specialist AI Review** — Agents for architecture, HTTP boundary, performance, dependency policy, and release readiness
- **Security Guards** — Blocks reading of secret files (`.env`, `.pem`, credentials, etc.)
- **Automated Dependency Updates** — Dependabot for both GitHub Actions and Deno dependencies

## Prerequisites

- [Docker](https://docker.com)
- [VS Code](https://code.visualstudio.com)
- [VS Code Remote - Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Quick Start

1. Open in VS Code
2. Run **Dev Containers: Clone Repository in Container Volume...** from the Command Palette
3. Select GitHub and search for this repository
4. Wait for the container to build
5. Set your `MINIMAX_API_KEY` environment variable in `.env`
6. Run **Dev Containers: Rebuild Container** to apply the new environmental values

## OpenCode AI Agents

| Agent                      | Purpose                                                       |
| -------------------------- | ------------------------------------------------------------- |
| `orchestrate`              | Orchestrates work, decomposes tasks, delegates to specialists |
| `deno-implementer`         | Makes code changes, prefers local tools, verifies scope       |
| `deno-reviewer`            | Architecture, modularity, dependency review                   |
| `deno-http-auditor`        | HTTP handler validation, response contracts                   |
| `deno-performance-auditor` | Memory safety, streaming, pagination, complexity              |
| `deno-release-manager`     | Pre-merge/release checklist                                   |

## Workflow Enforcement

The `deno-commands` plugin intercepts and redirects common Node.js/npm commands to their Deno equivalents:

| Blocked        | Redirected To |
| -------------- | ------------- |
| `npm run X`    | `deno task X` |
| `npm test`     | `deno test`   |
| `eslint`       | `deno lint`   |
| `prettier`     | `deno fmt`    |
| `tsc --noEmit` | `deno check`  |

## Environment Variables

This project is pre-configured to use MiniMax M2.7, but it's not a requirement. Any LLM supported by OpenCode can be used.

```env
MINIMAX_API_KEY=your_api_key_here
```

## License

MIT License — Copyright 2026 Isaac Jessup
