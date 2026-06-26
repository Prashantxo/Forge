# AGENTS

Cross-platform agent context for Forge. Read by Claude Code, Codex, Cursor,
Gemini CLI, and any tool supporting the AGENTS.md standard.

## Mission

Forge is an AI coding toolkit. Every skill, agent, and command targets one
goal: helping developers ship correct, secure, well-tested code faster.
Works with any model — cloud or local.

## Architecture

```
/codeforge:review  /codeforge:arch  /codeforge:tdd  /codeforge:docs  /codeforge:refine
        │
        ▼
  Forge Agent
  (codeforge-reviewer | codeforge-architect | codeforge-analyst)
        │
        ▼
  rules/model-adapter.md  →  tier: MAX | STANDARD | FAST
        │
        ▼
  Skill applied
  (review | secure | arch | tdd | agentic | docs | refine | eval | standards)
        │
        ▼
  Structured output → Human review
```

## Agents

| Agent | Capability needed | Role |
|-------|------------------|------|
| codeforge-reviewer | STANDARD or above | Code review — correctness, security, perf, tests |
| codeforge-architect | MAX preferred | Architecture — diagrams, ADRs, verdicts |
| codeforge-analyst | STANDARD or above | Research — adversarially verified, confidence-rated |

Agents inherit the active model from the host. No model IDs hardcoded.
Set `CODEFORGE_TIER=max|standard|fast` to override tier detection.

## Skills

| Skill | Brand color | Purpose |
|-------|------------|---------|
| review | #F97316 | Multi-dimensional code review |
| secure | #EF4444 | Security audit, OWASP Top 10 |
| arch | #8B5CF6 | Architecture review and design |
| tdd | #22C55E | Test-driven development |
| agentic | #06B6D4 | AI/LLM engineering patterns |
| docs | #3B82F6 | Documentation generation |
| refine | #F59E0B | Code simplification |
| eval | #EC4899 | Eval-driven development |
| standards | #6B7280 | Cross-project coding standards |

## Hard constraints

- No hardcoded secrets
- No production mutations without explicit human confirmation
- Tests required for all new functionality
- Evals required for all LLM feature changes
- Human review before executing agent output
