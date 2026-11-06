# AI Org Army 🏛️

A multi-agent AI organizational simulation for [Lou](https://lou.thomsonreuters.com) — dispatch a full company hierarchy (CEO → CTO → VPs → ICs) to tackle any goal with strategic planning, technical architecture, and hands-on execution.

## What It Does

Instead of one AI agent doing everything, AI Org Army dispatches **multiple agents** — each playing a distinct organizational role — to work on your goal simultaneously. You get multi-perspective thinking, proper delegation, and synthesized output.

```
┌─────────────────────────────────────┐
│          TIER 1: STRATEGIC          │
│     👑 CEO Strategist               │
│     ⚡ CTO Architect                │
│     💰 CFO Analyst                  │
├─────────────────────────────────────┤
│          TIER 2: MANAGEMENT         │
│     🔧 VP Engineering               │
│     📋 VP Product                   │
│     📢 VP Sales & Marketing         │
├─────────────────────────────────────┤
│          TIER 3: EXECUTION          │
│     💻 Senior Developer             │
│     🧪 QA Engineer                  │
│     🔒 Security Engineer            │
│     🔍 Research Analyst             │
└─────────────────────────────────────┘
```

## Quick Start

### Install as a Lou Skill

1. Copy the `skill/` folder contents to `~/.lou/skills/ai-org/`
2. Restart Lou or start a new chat
3. Say: *"Use ai-org to plan a SaaS product"*

Or install directly from [skills.thomsonreuters.com](https://skills.thomsonreuters.com) (once published).

### Usage Examples

| What You Say | What Happens |
|-------------|-------------|
| *"Use ai-org to plan a microservices migration"* | CEO + CTO + VP Product analyze strategy, architecture, and requirements |
| *"Army mode: build a REST API with auth"* | CTO + VP Eng + Developer + QA plan, build, and review the code |
| *"Use the org to research AI document processing tools"* | CEO + Research Analyst + VP Product investigate and recommend |
| *"Full org: launch a developer tool startup"* | All 7+ agents: strategy, architecture, product, code, QA, research |

## Task Auto-Detection

The skill automatically detects what kind of task you're asking for and picks the right team:

| Task Type | Trigger Keywords | Agents |
|-----------|-----------------|--------|
| **Planning** | plan, strategy, evaluate, roadmap | CEO + CTO + VP Product |
| **Build** | build, code, implement, create | CTO + VP Eng + Dev + QA |
| **Research** | research, compare, analyze | CEO + Research + VP Product |
| **Go-to-Market** | launch, marketing, growth, sell | CEO + VP Sales + CFO + Research |
| **Security** | security, audit, threats | CTO + Security Eng + QA |
| **Full Org** | army mode, full org, everything | All agents |

### Add-On Agents

Mention these keywords to automatically include extra agents:

- **"budget" / "cost" / "pricing"** → adds CFO Analyst
- **"security" / "auth" / "threats"** → adds Security Engineer
- **"marketing" / "launch" / "growth"** → adds VP Sales & Marketing

## The 10 Roles

### Tier 1 — Strategic

| Role | What They Do |
|------|-------------|
| **CEO Strategist** | Sets vision, success criteria, risk matrix, go/no-go, resource priorities |
| **CTO Architect** | Technical architecture, stack decisions, feasibility, data models, scaling |
| **CFO Analyst** | Cost analysis, revenue models, break-even, budget allocation, ROI |

### Tier 2 — Management

| Role | What They Do |
|------|-------------|
| **VP Engineering** | Task breakdown, dependency graphs, sprint plans, estimates |
| **VP Product** | User personas, user stories, feature maps, scope boundaries, UX principles |
| **VP Sales & Marketing** | GTM strategy, channel planning, growth loops, launch playbooks |

### Tier 3 — Execution

| Role | What They Do |
|------|-------------|
| **Senior Developer** | Production-quality code, tests, follows CTO architecture |
| **QA Engineer** | Code review, test cases, edge cases, security checks, quality verdict |
| **Security Engineer** | Threat modeling, OWASP Top 10, auth design, compliance |
| **Research Analyst** | Web research, competitive landscape, data points, recommendations |

## How It Works

```
You give a goal
       ↓
Lou detects task type
       ↓
Dispatches 3-7 agents (different AI models for diverse perspectives)
       ↓
Agents work independently, share findings via ledger
       ↓
Lou synthesizes all outputs into one cohesive deliverable
       ↓
You get a unified plan/code/analysis
```

### Error Handling

If agents can't connect (network issues), the skill falls back gracefully:

1. **Try direct models** (`sonnet-5`, `opus-4-6`) — most reliable
2. **Try AI Platform models** (`ai-platform-*`) — require SSO
3. **Try LiteLLM models** (`litellm-*`) — require VPN/ZScaler
4. **Single-agent fallback** — Lou delivers the full output itself

## Project Structure

```
ai-org-army/
├── README.md                          # This file
├── skill/                             # The Lou skill
│   ├── SKILL.md                       # Main skill definition (install this)
│   ├── scripts/
│   │   └── roles-config.json          # Role definitions, model routing, triggers
│   └── references/
│       └── quick-reference.md         # Cheat sheet for task detection
├── docs/
│   ├── architecture.md                # How the multi-agent system works
│   └── roles-deep-dive.md             # Detailed role prompt engineering guide
└── examples/
    └── sample-outputs/                # Example outputs from real runs
```

## Scaling with Paperclip AI

For persistent, 24/7 autonomous agents (beyond per-task dispatch), this project is designed to integrate with [Paperclip AI](https://www.paperclip.inc/) — an open-source orchestration platform for autonomous AI teams.

| Feature | Lou Skill (ai-org) | + Paperclip AI |
|---------|-------------------|----------------|
| Multi-agent dispatch | ✅ | ✅ |
| Role-based agents | ✅ | ✅ |
| Persistent 24/7 agents | ❌ | ✅ |
| Scheduled tasks | ❌ | ✅ |
| Budget tracking | ❌ | ✅ |
| Visual org chart | ❌ | ✅ |
| Cross-session memory | ❌ | ✅ |

See `docs/architecture.md` for the integration roadmap.

## Contributing

This skill is published on [skills.thomsonreuters.com](https://skills.thomsonreuters.com). Contributions welcome:

1. Fork this repo
2. Make your changes
3. Test with Lou
4. Submit a PR

Ideas for contribution:
- New agent roles (e.g., Data Engineer, UX Designer, Legal Counsel)
- Domain-specific variants (`ai-org-legal`, `ai-org-devops`)
- Better prompt templates
- Example outputs and case studies

## License

MIT

## Author

Built by [Nandini Sadiga](mailto:nandini.sadiga@thomsonreuters.com) with Lou.
