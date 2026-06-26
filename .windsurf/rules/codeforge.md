---
trigger: always_on
---

# CodeForge — AI Coding Toolkit

Apply CodeForge skills automatically based on task context.

## Skills

| Task | Skill |
|------|-------|
| Code review, PR review | codeforge:review |
| Security audit | codeforge:secure |
| Architecture review or design | codeforge:arch |
| New feature or bug fix | codeforge:tdd |
| Documentation | codeforge:docs |
| Code cleanup | codeforge:refine |
| AI/LLM feature | codeforge:eval |
| Code quality check | codeforge:standards |

## Review output format

```
[SEVERITY] category — title
File: path:line
Problem: one sentence
Fix: concrete action

Decision: BLOCK | REQUEST CHANGES | APPROVE WITH NOTES | APPROVE
CRITICAL: N  HIGH: N  MEDIUM: N  LOW: N
```

## Hard rules

- No hardcoded secrets — environment variables only
- Tests required for all new functionality
- Evals required before changing any LLM prompt
- Human review before executing agent output
- Structured logs with traceId on all external calls
