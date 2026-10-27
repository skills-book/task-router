# task-router

A Claude Code skill that routes every task to the cheapest model that can do it: mechanical
work to a Haiku subagent, lookups to a flat-cost research service, and only real thinking on
the main model.

## Tiers

| Work | Route |
|---|---|
| grep, list, read, rename, format, run a command, summarize logs, apply an exact edit | `cheap-worker` subagent (Haiku) |
| web lookup, docs, fact-check, page read | research service |
| design, architecture, debugging, security, multi-file change | main model |
| unsure | main model |

## Install

```sh
npx skills add skills-book/task-router --skill task-router -g
```

## Use

Nothing to call. Once installed, the skill triggers before coding, file, log, and research
tasks and sorts the work by itself. The first mechanical task copies the bundled
`cheap-worker` agent into `~/.claude/agents/`; after that the subagent is available in every
session.

## Codex CLI

Same idea: `.codex/agents/*.toml` with `model` and `model_reasoning_effort`. No Codex agent
file ships in v1 — Claude Code first.
