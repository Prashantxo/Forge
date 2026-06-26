---
inclusion: always
---

# CodeForge — AI Coding Toolkit

Forge provides structured workflows for code review, security, TDD, architecture, docs, and evals.

## Skill routing

| Context | Skill to apply |
|---------|---------------|
| Reviewing code or PR | codeforge:review |
| Code touches auth, inputs, secrets, APIs | codeforge:secure |
| Architecture or system design | codeforge:arch |
| New feature or bug | codeforge:tdd |
| Documentation needed | codeforge:docs |
| Simplifying recent changes | codeforge:refine |
| LLM feature changing | codeforge:eval |
| Code quality or new module | codeforge:standards |

## Review output format

```
[SEVERITY] category — title
File: path:line
Problem: one sentence
Fix: concrete action

Decision: BLOCK | REQUEST CHANGES | APPROVE WITH NOTES | APPROVE
CRITICAL: N  HIGH: N  MEDIUM: N  LOW: N
```

## Principles

1. Tests before code
2. Evals before LLM changes
3. Plan before implementation
4. No hardcoded secrets
5. Structured logs with traceId on all external calls
6. Human review before executing agent output
