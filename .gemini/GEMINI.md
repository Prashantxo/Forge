# CodeForge for Gemini CLI

Model-adaptive AI coding toolkit. Skills auto-load from `skills/`.

## Core workflow

1. Tests before code — use `codeforge:tdd`
2. Review before merge — use `codeforge:review`
3. Security scan before release — use `codeforge:secure`
4. Evals before any LLM feature change — use `codeforge:eval`

## Standards

- Strong typing. No `any`.
- Structured logging with trace IDs.
- No hardcoded secrets — use environment variables.
- Validate all user input at system boundaries.
