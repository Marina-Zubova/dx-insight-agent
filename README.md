# DX Insight Agent

A Developer Experience research agent that continuously analyzes GitHub pull requests to identify friction in software development workflows.

## What It Does

- **Job A** (every 6h): Analyzes newly merged pull requests from [huggingface/transformers](https://github.com/huggingface/transformers) and produces DX Friction Reports
- **Job B** (daily): Aggregates findings into a Repository DX Summary identifying recurring patterns

## Methodology

This agent treats pull request analysis as UX research rather than code review. It focuses on:

- Developer behavior and collaboration patterns
- Where developers lose time and effort
- Observable evidence from PR discussions, timelines, and review comments
- Recurring DX themes: Documentation, Tooling, Communication, Process, Onboarding, Testing, CI/CD, Code Review

## Repository Structure

```
├── AGENTS.md              # Agent permissions & guardrails
├── IDENTITY.md            # Agent identity configuration
├── HEARTBEAT.md           # Scheduled tasks
├── MEMORY.md              # Long-term memory & preferences
├── SOUL.md                # Agent personality & behavior
├── USER.md                # Researcher profile
├── dx-analysis-state.md   # PR tracking state
└── reports/
    ├── pr-*.md            # Individual PR friction reports
    ├── batch1-improved.md # Batch analysis (self-critique improved)
    └── repo-summary-*.md  # Daily/weekly repository DX summaries
```

## Reports

### Batch 1 (2026-06-27)
- **5 PRs analyzed:** #43838, #46473, #46565, #46865, #46923
- **Key findings:** Modular system limitations, CI security gate UX, undocumented pitfalls, test infrastructure as onboarding barrier

See [reports/repo-summary-2026-06-27.md](reports/repo-summary-2026-06-27.md) for the full summary.

## Guardrails

- Read-only: observes and analyzes, never modifies repositories
- Evidence-based: every finding supported by GitHub artifacts
- DX research lens: focuses on developer experience, not code quality
- Never analyzes the same PR twice

## Setup

This agent runs on [OpenClaw](https://openclaw.ai) with scheduled cron jobs for continuous monitoring.
