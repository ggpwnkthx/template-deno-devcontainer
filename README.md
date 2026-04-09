# Deno Dev Container Template

A ready-to-use Deno development environment with AI coding assistance powered by [OpenCode](https://opencode.ai).

## What's Inside

- **Deno runtime**: Official `denoland/deno` image with everything set up
- **OpenCode AI**: AI pair programmer configured with MiniMax M2.7 (or swap in any OpenAI-compatible model)
- **Node blocker**: Blocked commands like `npm`, `npx`, and `pnpm` redirect to Deno equivalents to keep you in a native workflow
- **Auto-formatting**: `deno fmt`, `deno lint`, and `deno check` run automatically after saves
- **AI review agents**: Architecture, HTTP boundaries, performance, dependencies, and release readiness
- **Secret protection**: Blocks accidental reads of `.env`, `.pem`, and credential files
- **Dependabot**: Keeps GitHub Actions and Deno dependencies up to date

## Prerequisites

- [Docker](https://docker.com)
- [VS Code](https://code.visualstudio.com)
- [VS Code Remote - Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Getting Started

1. Open this repository in VS Code
2. Run **Dev Containers: Clone Repository in Container Volume...** from the Command Palette
3. Choose GitHub and search for this repository
4. Wait for the container to build
5. Create a `.env` file in the root with your API key:

   ```env
   MINIMAX_API_KEY=your_api_key_here
   ```

6. Run **Dev Containers: Rebuild Container** so the environment variable is available inside the container
7. Open a new Terminal and run `opencode` to start the AI assistant

## AI Agents

These agents run inside OpenCode to help with different aspects of your code:

| Agent                      | What it does                                                      |
| -------------------------- | ----------------------------------------------------------------- |
| `orchestrate`              | Breaks down tasks and coordinates the other agents                |
| `deno-implementer`         | Writes and edits code, prefers local Deno tools                   |
| `deno-reviewer`            | Reviews architecture, modularity, and dependency structure        |
| `deno-http-auditor`        | Checks HTTP handlers for validation and response contracts        |
| `deno-performance-auditor` | Looks for memory issues, missing streams, and complexity problems |
| `deno-release-manager`     | Runs pre-release checks before merging                            |

## Staying in a Deno-Native Workflow

Commands that don't exist in Deno are intercepted and redirected:

| Instead of     | Use           |
| -------------- | ------------- |
| `npm run X`    | `deno task X` |
| `npm test`     | `deno test`   |
| `eslint`       | `deno lint`   |
| `prettier`     | `deno fmt`    |
| `tsc --noEmit` | `deno check`  |

This keeps you from accidentally dropping into a Node.js workflow while working in a Deno project.

## Model Configuration

The default model is MiniMax M2.7, but any LLM supported by OpenCode works. Set your API key in `.env` as shown above.

## License

MIT License: Copyright 2026 Isaac Jessup
