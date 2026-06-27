# HEARTBEAT.md

tasks:

* name: dx-analyze-prs
  interval: 6h
  prompt: "Check the huggingface/transformers repository for newly merged pull requests that have not yet been analyzed. Produce a DX Friction Report for each new PR and update dx-analysis-state.md. If there are no new merged PRs, do nothing."

* name: dx-weekly-summary
  interval: 24h
  prompt: "Review all DX Friction Reports generated since the last summary. Identify recurring Developer Experience patterns, common blockers, communication issues, documentation gaps, onboarding problems, and process bottlenecks. Generate a Repository DX Report and update dx-analysis-state.md."
