---
description: CodeForge AI coding toolkit — review, security, TDD, architecture, docs, evals
---

# CodeForge

Apply CodeForge skills automatically:

| Task | Skill |
|------|-------|
| Code review or PR | codeforge:review |
| Security audit | codeforge:secure |
| Architecture | codeforge:arch |
| New feature or bug fix | codeforge:tdd |
| Documentation | codeforge:docs |
| Code cleanup | codeforge:refine |
| AI/LLM feature | codeforge:eval |
| Code quality | codeforge:standards |

## Output format

```
[SEVERITY] category — title
File: path:line
Problem: one sentence
Fix: concrete action

Decision: BLOCK | REQUEST CHANGES | APPROVE WITH NOTES | APPROVE
```

## Rules

- No hardcoded secrets
- Tests before code
- Evals before LLM changes
- Structured logs with traceId on all external calls
