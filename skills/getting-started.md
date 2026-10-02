# Getting Started: JEV-Trader Onboarding

First-run onboarding flow for setting up JEV-Trader with a new operator or desk instance.

## Onboarding Sequence

Ask the following questions **one at a time**. Never batch multiple questions or request secrets in chat.

### 1. Operator Name
"What's your name or handle?"

Store for personalized interactions and commit attribution if needed.

### 2. Desk Repository
"What's your desk repository URL (e.g., https://github.com/your-org/jev-desk)?"

Confirms where the application code lives. Look for `GROK_HANDOFF.md` there.

### 3. Service Topology
"How are you running the judge, shadow, and CDP services?"

- Local ports?
- Docker containers?
- Remote instances?

Store the topology map (e.g., judge on `:8080`, shadow on `:3000`).

### 4. Judge Configuration
"Is your judge running with `mock: false` or `mock: true`?"

Production should be `mock: false`. Development/staging may use mock mode.

### 5. Operations Endpoints
"Where is your `/ops` endpoint and `state.json` file?"

Typically `/ops` on the main desk server and `state.json` in the project root or data directory.

### 6. FOMO/CDP Setup
"How is your FOMO tracker connecting to Chrome?"

- CDP endpoint URL?
- Local vs. remote browser?
- Headless or headed?

### 7. Standing Rules Review
"Any custom standing rules or conventions I should follow for your desk?"

Examples:
- Specific PR review requirements
- Test coverage thresholds
- Deployment gates
- On-call protocols

### 8. Confirmation
"I've recorded your setup. Ready to start monitoring the desk?"

Summarize the configuration and confirm the bot is ready.

## Security Reminder

**Never ask for secrets, API keys, tokens, or credentials in chat.**

If authentication is needed, guide the operator to:
- Add secrets via Cursor Dashboard (Cloud Agents > Secrets)
- Use environment variables
- Reference secure credential stores

## Next Steps

After onboarding:
1. Read `GROK_HANDOFF.md` from the desk repository
2. Check `/api/state` or `state.json` for current cycle metrics
3. Verify judge health (age gate, judged count)
4. Confirm FOMO tracker connectivity
5. Review any open PRs or issues in the desk repo
