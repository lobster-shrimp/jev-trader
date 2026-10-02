# JEV-Trader

Cursor/Grok bot that helps run and improve a memecoin launch desk — shadow cycles, judge service, FOMO/Gecko tracking, risk book, and ops panel.

**This repository contains the bot recipe and handoff documentation.** The actual desk application code lives in a separate repository (e.g., [lobster-shrimp/jev-desk](https://github.com/lobster-shrimp/jev-desk)).

## What It Does

JEV-Trader is a Cursor/Grok assistant configured to:
- Monitor and coordinate shadow trading cycles
- Track judge service health and age gate logic
- Interface with FOMO tracking via Chrome DevTools Protocol (CDP)
- Review and update the risk book
- Maintain the operations panel (`/ops`)
- Submit code improvements via cloud agents and pull requests
- Never expose secrets or approve its own PRs
- Work with real cycle data only (`demo: false`)

## How to Use

1. **Load the bot role**: Follow the instructions in `AGENT.md`
2. **Run first-time setup**: The bot will walk through onboarding (see `skills/getting-started.md`)
3. **Provide context**: Point the bot to your desk repository and running services
4. **Iterate**: Use cloud agents for code changes, local ops for restarts and logs

The bot reads conventions from `memories.md` and follows standing rules defined in your handoff.

## Standing Rules

- **No secrets in chat**: Never print tokens, env vars, or credentials
- **Real data only**: Always use `demo: false` for cycle operations
- **PR workflow**: Cloud agents create PRs; humans review and merge
- **CI gate**: Merge when CI is green (bot can land fixes autonomously when appropriate)
- **Ops access**: Use `/ops` endpoint and `state.json` for runtime inspection

## Ops Notes

### Age Gate
Free age typically ranges from ~15 minutes to 72 hours. A healthy judge with `judged=0` and positive free age means the judge is running but no tokens have been processed yet.

### Operations Panel
The `/ops` endpoint exposes:
- Current cycle state
- Judge health and age metrics
- FOMO tracker status
- Risk book summary

### Judge Health
Judge service typically runs on port `:8080` with `mock: false` in production. Check age gate and judged count to verify it's processing tokens.

## Related Repositories

- **Desk Application**: The trading desk code lives in a sibling repository (e.g., `lobster-shrimp/jev-desk`)
- **This Repo**: Bot recipe, role prompt, conventions, and onboarding

## License

MIT
