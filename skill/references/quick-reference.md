# AI-Org Quick Reference

## Task Type Detection Cheat Sheet

| User Says | Task Type | Agents Dispatched |
|-----------|-----------|-------------------|
| "plan", "strategy", "should we" | PLANNING | CEO + CTO + VP Product |
| "build", "code", "implement" | BUILD | CTO + VP Eng + Dev + QA |
| "research", "compare", "analyze" | RESEARCH | CEO + Research + VP Product |
| "launch", "go-to-market", "growth" | GTM | CEO + VP Sales + CFO + Research |
| "security", "audit", "vulnerabilities" | SECURITY | CTO + Security Eng + QA |
| "army mode", "full org", "everything" | FULL ORG | All 7+ agents |

## Add-On Triggers

| User Mentions | Add This Agent |
|---------------|----------------|
| "budget", "cost", "pricing" | CFO Analyst |
| "security", "auth", "threats" | Security Engineer |
| "marketing", "launch", "growth" | VP Sales & Marketing |

## Model Routing (Priority Order)

| Agent Tier | First Try | Fallback |
|------------|-----------|----------|
| Strategic (CEO, CTO, CFO) | ai-platform-opus-5 | litellm-opus-5 |
| Management (VPs) | ai-platform-gpt-5-6-luna | litellm-sonnet-5 |
| Execution (Dev, QA, Security) | ai-platform-sonnet-5 | litellm-sonnet-5 |
| Research | ai-platform-gemini-2-5-pro | litellm-gemini-3-1 |

## Fallback Chain
1. Try `ai-platform-*` models (SSO auth)
2. Try `litellm-*` models (ZScaler/VPN required)
3. Try `ollama` (local, if configured)
4. Single-agent mode (Lou does everything)
