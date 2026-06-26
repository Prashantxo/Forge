# Changelog

All notable changes follow [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
Versions follow [Semantic Versioning](https://semver.org/).

## [1.0.3] - 2026-06-26

### Changed
- Brand name casing: Codeforge → CodeForge across all docs and display names

## [1.0.2] - 2026-06-26

### Changed
- Complete rename: all agent names, platform config files, repo URLs, env var, brand text updated to CodeForge
- Renamed agent files: forge-* → codeforge-*
- Renamed platform config files: forge.md → codeforge.md (Windsurf, Kiro, Cline)
- FORGE_TIER env var → CODEFORGE_TIER

## [1.0.1] - 2026-06-26

### Changed
- Renamed plugin from `forge` to `codeforge` to avoid marketplace name collision with existing `forge` plugin

## [1.0.0] - 2026-06-24

### Added
- 8 slash commands: `/codeforge:review`, `/codeforge:secure`, `/codeforge:arch`, `/codeforge:tdd`, `/codeforge:docs`, `/codeforge:refine`, `/codeforge:eval`, `/codeforge:standards`
- 9 skills: `review`, `secure`, `arch`, `tdd`, `agentic`, `docs`, `refine`, `eval`, `standards`
- 3 agents: `codeforge-reviewer`, `codeforge-architect`, `codeforge-analyst`
- Model-adaptive tier routing via `rules/model-adapter.md`: MAX / STANDARD / FAST
- `CODEFORGE_TIER` env var override
- Cross-platform support: Claude Code, Codex, Gemini CLI, Cursor, Windsurf, Zed, Kiro, Cline, Aider
- Hooks: destructive-command blocker, post-write secret scanner
- MCP config: GitHub + filesystem
- Each skill includes `agents/openai.yaml` for Codex cross-platform use
- CI pipeline: 6-job workflow validating all 9 platforms, structural tests, security scan, final gate
- 101-check test suite (`tests/validate-structure.sh`)
