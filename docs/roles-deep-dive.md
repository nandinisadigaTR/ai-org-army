# Roles Deep Dive — Prompt Engineering Guide

This document explains the design decisions behind each agent's prompt and how to customize them.

## Prompt Design Principles

1. **Self-contained** — Each agent sees ONLY its prompt. No conversation context. Include everything it needs.
2. **Goal verbatim** — Always paste the user's exact goal. Don't paraphrase.
3. **Numbered deliverables** — Agents produce better output when given a clear numbered list of expected outputs.
4. **Personality directives** — "Be decisive", "Be skeptical", "Be user-centric" shape the agent's behavior.
5. **Web search encouragement** — Agents with research needs should be told to search the web.
6. **Ledger awareness** — Agents should be told to check the ledger for other agents' work and share their own.

## Role Customization Guide

### Adding a New Role

1. Define the role in `SKILL.md` under Agent Prompt Templates
2. Add the role to `scripts/roles-config.json` with:
   - `title` — display name
   - `mode` — scout or worker
   - `tier` — strategic, management, or execution
   - `model_priority` — ordered list of preferred models
   - `triggers` — keywords that activate this role
3. Add the role to relevant task patterns in `scripts/roles-config.json`

### Example: Adding a UX Designer Role

```
### UX Designer
You are a UX Designer. Your job is user experience and interface design.

THE GOAL: {user's goal verbatim}

Your deliverables:
1. USER FLOWS — Key user journeys mapped out step by step
2. WIREFRAMES — Describe screen layouts in detail (text-based wireframes)
3. INTERACTION PATTERNS — How users interact with each feature
4. ACCESSIBILITY — WCAG compliance considerations
5. DESIGN SYSTEM — Component library recommendations

Check the ledger for VP Product's user stories. Your designs should map to their requirements.
Be opinionated about UX. Simplicity over feature density. Speed over decoration.
```

### Example: Adding a Data Engineer Role

```
### Data Engineer
You are a Data Engineer. Your job is data architecture and pipeline design.

THE GOAL: {user's goal verbatim}

Your deliverables:
1. DATA MODEL — Entities, relationships, normalization decisions
2. PIPELINE DESIGN — ETL/ELT flows, data sources, transformations
3. STORAGE STRATEGY — Which databases for which data? Why?
4. QUERY PATTERNS — Most common queries and how to optimize them
5. DATA GOVERNANCE — PII handling, retention policies, compliance

Check the ledger for the CTO's architecture. Your data layer should integrate with their design.
Be practical. Optimize for the queries you'll actually run, not theoretical perfection.
```

## Tuning Tips

- **Agent too verbose?** Add: "Keep each section under 200 words. Be concise."
- **Agent too generic?** Add domain context: "This is for a fintech SaaS serving hedge funds."
- **Agent not using web search?** Add: "You MUST search the web for current data before answering."
- **Agents not coordinating?** Add: "Check the ledger FIRST before starting your analysis."
- **Output quality low?** Use a higher-tier model (opus instead of sonnet).
