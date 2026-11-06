# Architecture — AI Org Army

## System Overview

AI Org Army is a multi-agent orchestration skill for Lou that simulates a company hierarchy to tackle complex goals.

## How Multi-Agent Dispatch Works

```
┌──────────────────────────────────────────────┐
│                    USER                       │
│          "Plan a SaaS product"               │
└──────────────┬───────────────────────────────┘
               │
               ▼
┌──────────────────────────────────────────────┐
│               LOU (Parent Agent)              │
│                                              │
│  1. Load ai-org skill                        │
│  2. Detect task type (PLANNING)              │
│  3. Select agents: CEO + CTO + VP Product    │
│  4. Choose models (diverse mix)              │
│  5. Dispatch agents with self-contained      │
│     prompts including the goal               │
└──┬───────────┬───────────┬───────────────────┘
   │           │           │
   ▼           ▼           ▼
┌────────┐ ┌────────┐ ┌────────┐
│  CEO   │ │  CTO   │ │  VP    │
│ opus   │ │ sonnet │ │ sonnet │
│        │ │        │ │        │
│Strategy│ │Arch    │ │Product │
│Risk    │ │Stack   │ │Stories │
│Go/NoGo │ │Data    │ │Scope   │
└───┬────┘ └───┬────┘ └───┬────┘
    │          │          │
    ▼          ▼          ▼
┌──────────────────────────────────────────────┐
│            SHARED LEDGER                      │
│                                              │
│  Agents share findings, read each other's    │
│  work, and coordinate via append-only log    │
└──────────────┬───────────────────────────────┘
               │
               ▼
┌──────────────────────────────────────────────┐
│           LOU (Synthesis)                     │
│                                              │
│  1. Read all ledger entries                  │
│  2. Identify agreements & conflicts          │
│  3. Resolve conflicts                        │
│  4. Present unified deliverable              │
└──────────────────────────────────────────────┘
```

## Agent Modes

- **Scout** — Read-only. Can search, read files, analyze. Cannot write files. Used for strategy, research, review roles.
- **Worker** — Full access. Can read, write files, run shell commands. Used for developer role (scoped to project files).

## Model Diversity

Different AI models bring different perspectives:

| Model | Strengths | Used For |
|-------|-----------|----------|
| opus-4-6 / opus-5 | Deep reasoning, nuance | CEO, CTO, Security |
| sonnet-5 | Fast, capable, balanced | VPs, Dev, QA |
| sonnet-4-6 | Reliable, cost-effective | Supporting roles |
| haiku-4-5 | Ultra-fast | Quick research, simple tasks |

Mixing Claude + GPT models across agents provides genuinely different viewpoints.

## Fallback Chain

```
Direct models (sonnet-5, opus-4-6)
        │ fail?
        ▼
AI Platform models (ai-platform-*)
        │ fail?
        ▼
LiteLLM models (litellm-*)
        │ fail?
        ▼
Single-agent mode (Lou does everything)
```

## Future: Paperclip AI Integration

The current system is session-based (agents exist for one task). For persistent autonomous operation:

1. Export role prompts → Paperclip agent templates
2. Build org chart in Paperclip UI
3. Set schedules (daily standups, weekly reviews)
4. Connect tools (GitHub, Slack, databases)
5. Agents run 24/7 independently

This repo will include Paperclip configuration templates in a future release.
