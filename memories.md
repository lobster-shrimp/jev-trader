# JEV-Trader Conventions

Scrubbed convention bullets derived from operational handoffs and briefings.

## Handoff Briefing

- Start from `GROK_HANDOFF.md` in the desk repository for full context
- Desk handles shadow cycles, judge service, FOMO/Gecko tracking, risk book, ops panel
- Bot assists with ops monitoring and code improvements via PRs

## Operations State

- Read ops from `state.json` or `/api/state` endpoint
- Free age ~15m–72h explains `judged=0` with healthy judge (waiting for tokens)
- Judge age gate: positive free age means service is running correctly
- Age gate reset indicates judge processed tokens recently

## Service Health

- **Judge**: Often runs on `:8080` with `mock: false` in production
- **FOMO tracking**: Via Chrome CDP connection
- **Ops panel**: `/ops` exposes cycle state, judge metrics, risk book
- Check `judged` count and age metrics to verify judge is processing

## GitHub Workflow

- Use Cursor tools for pull requests
- Cloud agents handle code changes
- Never self-approve PRs
- Merge when CI is green
- Land fixes autonomously when appropriate and tests pass

## Data Rules

- Real cycle data only: always `demo: false`
- Never print secrets or tokens in chat
- Verify cycle state from `/api/state` before operations
- Trust `state.json` as ground truth for metrics

## Desk Architecture

- Shadow cycles: automated token launch monitoring
- Judge service: evaluates tokens and manages age gate
- Risk book: tracks exposure and position limits
- FOMO tracker: monitors Gecko and social signals
- Ops panel: unified runtime view

## First-Run Setup

- Ask for operator name, desk repo URL, service topology
- Confirm how judge/shadow/CDP are running
- Review standing rules one at a time
- Never ask for secrets in chat
