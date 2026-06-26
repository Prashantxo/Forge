<div align="center">

# ⚒️ CodeForge

**An AI coding toolkit that fits into how you already work.**

[![Version](https://img.shields.io/badge/v1.0.0-orange?style=flat-square&logo=github&logoColor=white)](https://github.com/Prashantxo/CodeForge/releases)
[![License](https://img.shields.io/badge/MIT-green?style=flat-square&logo=opensourceinitiative&logoColor=white)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-blueviolet?style=flat-square&logo=anthropic&logoColor=white)](https://claude.ai/code)
[![OpenAI Codex](https://img.shields.io/badge/Codex-black?style=flat-square&logo=openai&logoColor=white)](https://openai.com/codex)
[![Gemini CLI](https://img.shields.io/badge/Gemini%20CLI-4285F4?style=flat-square&logo=google&logoColor=white)](https://github.com/google-gemini/gemini-cli)
[![Cursor](https://img.shields.io/badge/Cursor-orange?style=flat-square&logo=cursor&logoColor=white)](https://cursor.com)

[![Stars](https://img.shields.io/github/stars/Prashantxo/CodeForge?style=flat-square&logo=github&color=yellow)](https://github.com/Prashantxo/CodeForge/stargazers)

8 slash commands &nbsp;·&nbsp; 9 skills &nbsp;·&nbsp; 3 agents &nbsp;·&nbsp; works with any LLM

</div>

---

```
/codeforge:review

[CRITICAL] security — Hardcoded API key in source
File: src/api/client.ts:14
Problem: API key assigned to const — committed to version control
Fix: Move to process.env.API_KEY, add to .gitignore

[HIGH] correctness — Off-by-one in pagination
File: src/lib/paginate.ts:42
Problem: Loop runs to items.length instead of items.length - 1
Fix: Change loop condition to i < items.length - 1

Decision: BLOCK
CRITICAL: 1  HIGH: 1  MEDIUM: 2  LOW: 0
```

---

## What is CodeForge?

Tired of writing the same review prompts over and over? CodeForge is a Claude Code plugin that gives you proper commands for the things you do every day: code review, security audits, TDD, architecture planning, docs, and more. Each one has a consistent output format and a clear ship/block verdict.

It works with whatever model you're running — Claude, GPT-4o, Gemini, or a local model like Llama or Mistral. You don't have to change anything.

---

## Install

**One-click via claude.com:**
Go to [claude.com/plugins](https://claude.com/plugins), search **CodeForge**, hit **Install in Claude Code**.

**Official marketplace (coming soon):**
```
/plugin install codeforge@claude-plugins-official
```

**Via GitHub:**
```bash
claude plugin install Prashantxo/CodeForge
```

**Via Claude Plugin Hub:**
```bash
npx claudepluginhub install codeforge
```

**Manual:**
```bash
git clone https://github.com/Prashantxo/CodeForge
cd codeforge
claude plugin validate
```

---

## Commands

| Command | What it does |
|---------|-------------|
| `/codeforge:review` | Reviews your diff or a PR. Returns severity-rated findings and a ship verdict. |
| `/codeforge:secure` | OWASP Top 10 audit. Covers secrets, injection, auth, supply chain. |
| `/codeforge:arch` | Reviews existing architecture or designs a new one from your description. |
| `/codeforge:tdd` | Writes failing tests first, waits for your approval, then implements. |
| `/codeforge:docs` | Generates README, API reference, architecture doc, or runbook. |
| `/codeforge:refine` | Simplifies changed code without touching behavior. |
| `/codeforge:eval` | Defines pass/fail criteria before you touch any LLM feature. |
| `/codeforge:standards` | Checks naming, types, error handling, and observability patterns. |

---

## Skills

Skills load automatically based on what you're doing. No manual activation.

| Skill | Activates when |
|-------|---------------|
| `codeforge:review` | Reviewing PRs or changed files |
| `codeforge:secure` | Code touches auth, inputs, APIs, payments, or secrets |
| `codeforge:arch` | Designing or evaluating system architecture |
| `codeforge:tdd` | Writing new features or fixing bugs |
| `codeforge:agentic` | Building agents, prompts, MCP servers, evals, or RAG pipelines |
| `codeforge:docs` | Generating documentation of any kind |
| `codeforge:refine` | Cleaning up recently changed code |
| `codeforge:eval` | Shipping or changing any LLM-powered feature |
| `codeforge:standards` | Code quality review or setting up a new module |

---

## Agents

| Agent | Best with | Does |
|-------|-----------|------|
| `codeforge-reviewer` | Any model | Code review across 6 dimensions |
| `codeforge-architect` | MAX tier preferred | Architecture diagrams, ADRs, verdicts |
| `codeforge-analyst` | Any model | Deep research with adversarial verification |

Agents inherit whatever model you're running. No model names hardcoded anywhere.

---

## Works across model tiers

CodeForge detects what your model can do and adjusts depth accordingly. Override anytime with `CODEFORGE_TIER=max|standard|fast`.

| Tier | When it kicks in | What you get |
|------|-----------------|--------------|
| MAX | Frontier reasoning models | Full depth, all phases, detailed findings |
| STANDARD | Mid-range models (default) | Full phases, concise output |
| FAST | Lightweight / local models | 3 phases, bullets, CRITICAL + HIGH only |

Same severity labels and verdict format across all tiers.

---

## Platform support

| Platform | Config it reads | Hooks |
|----------|----------------|-------|
| Claude Code | `.claude-plugin/plugin.json` + `CLAUDE.md` | `hooks/hooks.json` |
| OpenAI Codex | `.codex-plugin/plugin.json` + `AGENTS.md` | none |
| Gemini CLI | `.gemini/GEMINI.md` | none |
| Cursor | `.cursor/hooks.json` | `.cursor/hooks.json` |
| Windsurf | `.windsurfrules` + `.windsurf/rules/codeforge.md` | none |
| Zed | `.rules` + `AGENTS.md` | none |
| Kiro | `.kiro/steering/codeforge.md` | `.kiro/hooks/` |
| Cline | `.clinerules/codeforge.md` | `.clinerules/hooks/` |
| Aider | `.aider.conf.yml` + `AGENTS.md` | none |

---

## The workflow

```
DISCOVER    /codeforge:arch    understand the problem
DESIGN      /codeforge:arch    plan before writing code
TEST        /codeforge:tdd     write failing tests first
IMPLEMENT   /codeforge:tdd     make the tests pass
EVAL        /codeforge:eval    define pass/fail for AI features
REVIEW      /codeforge:review  + /codeforge:secure
REFINE      /codeforge:refine  clean up, no behavior change
DOCS        /codeforge:docs    README, API ref, runbook
RELEASE     human review of all findings
```

---

## Quick examples

```bash
# Review a PR
/codeforge:review 142

# Review your current changes
/codeforge:review

# Audit a specific file
/codeforge:secure src/auth/middleware.ts

# Design a new system
/codeforge:arch add rate limiting in front of the API gateway

# Start a TDD cycle
/codeforge:tdd user can reset password via email link

# Generate API docs
/codeforge:docs src/api/

# Simplify recent changes
/codeforge:refine

# Set up evals before touching a prompt
/codeforge:eval summarization pipeline
```

---

## How CodeForge approaches things

- Write the failing test before writing the feature
- Define eval criteria before touching any LLM prompt
- Sketch the design before writing any code
- Use MCP instead of one-off custom integrations
- Use agents instead of stuffing everything into one giant context
- Run a security pass before every release
- No hardcoded secrets, period
- Structured logs and trace IDs from the start, not bolted on later

---

## File structure

```
codeforge/
├── .claude-plugin/plugin.json     Claude Code manifest
├── .codex-plugin/plugin.json      Codex manifest
├── .gemini/GEMINI.md              Gemini CLI context
├── .cursor/hooks.json             Cursor hooks
├── rules/model-adapter.md         Tier routing for every command
├── commands/                      8 slash commands
├── skills/                        9 skills (SKILL.md + openai.yaml each)
├── agents/                        3 specialized agents
├── hooks/                         Destructive-command blocker + secret scanner
├── .mcp.json                      GitHub + filesystem MCP
├── CLAUDE.md
└── AGENTS.md
```

---

## Add your own skill

```
skills/<name>/SKILL.md             Instructions (table-first format)
skills/<name>/agents/openai.yaml   Cross-platform metadata
```

Then run `claude plugin validate` before opening a PR. See [CONTRIBUTING.md](CONTRIBUTING.md) for the full guide.

---

## Requirements

- Claude Code (latest), or any AGENTS.md-compatible tool
- `GITHUB_TOKEN` env var (only needed for `/codeforge:review` with a PR number)

---

## Troubleshooting

**Skills not loading**
Run `claude plugin validate`. Check that `.claude-plugin/plugin.json` points to `./skills/` and `./commands/`.

**`/codeforge:review 142` fails with an auth error**
`GITHUB_TOKEN` isn't set. Run `export GITHUB_TOKEN=ghp_...` or add it to your `.env`.

**Output is too brief or too verbose**
Tier is auto-detected. Force it with `export CODEFORGE_TIER=max` (or `standard` or `fast`).

**A hook blocked a command it shouldn't have**
Check `hooks/hooks.json` and add an allowlist entry for the pattern. Don't disable hooks globally.

**`claude plugin install` can't find the repo**
Make sure the repo is public and the slug is exact: `claude plugin install Prashantxo/CodeForge`.

---

## FAQ

**Does this work with local models?**
Yes. Set `CODEFORGE_TIER=fast` for models with smaller context windows.

**Does it work outside Claude Code?**
Skills load in any tool that reads `AGENTS.md` (Codex, Cursor, Gemini CLI). Slash commands need Claude Code.

**Can I use just one or two skills?**
Yes. Source individual `skills/<name>/SKILL.md` files directly in your `CLAUDE.md`.

**Does CodeForge send my code anywhere?**
No. It's prompt instructions and config files. Everything runs inside your AI tool. The only network calls are from MCP servers you explicitly configure.

**How do I update?**
```bash
claude plugin update codeforge
# or, if installed manually:
git pull origin main
```

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

1. Fork and clone
2. Add a skill: `skills/<name>/SKILL.md` + `skills/<name>/agents/openai.yaml`
3. Run `claude plugin validate`
4. Open a PR, one skill per PR

---

## License

[MIT](LICENSE)
