# Demo Script — Live PR Analysis

**Duration:** 3-4 minutes  
**PR:** #46473 — fix(cli/serve): import serve handlers lazily so the CLI works without the `serve` extra

---

## Setup (before talk)
- Have OpenClaw session open in a separate browser tab
- Clear the terminal / chat so the audience sees a fresh session
- Have the PR page open: https://github.com/huggingface/transformers/pull/46473

---

## Demo Flow

### 1. Introduce the PR (30s)
> "Let's watch the agent analyze a real PR. This is PR 46473 — a contributor tried to fix a CLI crash when the optional `serve` extra wasn't installed."

### 2. Trigger the agent (10s)
Type in the OpenClaw chat:
```
Analyze PR #46473 from huggingface/transformers for DX friction
```

### 3. Narrate what's happening (2 min)
As the agent works, narrate the steps:
- **"First it pulls the PR metadata"** — author, dates, size
- **"Now it's reading the review comments"** — watch it fetch reviews and inline comments
- **"It's found something"** — the agent will surface the `from __future__ import annotations` pitfall
- **"Notice it's quoting evidence"** — point out the direct quote from LysandreJik
- **"It's cross-referencing prior PRs"** — the agent links to #44256 and #44620

### 4. Key moment — the friction finding (30s)
The agent will produce something like:
> "The contributor used `from __future__ import annotations`, which silently breaks FastAPI. This same pitfall was hit in PRs #44256 and #44620. Three PRs hitting the same undocumented anti-pattern."

> "See that? Three PRs. Same pitfall. Zero documentation. That's the kind of pattern a human reviewer might notice once, but an agent catches every time."

### 5. Show the categorization (30s)
> "Notice how it categorizes: Documentation, Onboarding, CI/CD. It's not judging code quality — it's asking 'where did the developer lose time?'"

### 6. Transition back to slides (10s)
> "And it does this every 6 hours, automatically. Let me show you what it found across 5 PRs..."

---

## Fallback Plan
If the live demo is slow or fails:
- Have the agent's output from `reports/batch1-improved.md` pre-loaded
- Show the saved report and walk through the findings manually
- Key quote to show: LysandreJik's `from __future__ import annotations` comment

---

## Risk Mitigation
- **API rate limits:** The agent uses unauthenticated GitHub API (60 req/hr). Should be fine for one PR.
- **Slow response:** If the agent takes >60s, switch to the saved report.
- **Wrong PR analyzed:** The agent is deterministic given the same input — test beforehand.
