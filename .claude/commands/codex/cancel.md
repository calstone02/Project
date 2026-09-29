---
description: Cancel an active background Codex job in this repository
argument-hint: '[job-id]'
disable-model-invocation: true
allowed-tools: Bash(node:*)
---

!`node ".claude/codex-plugin/scripts/codex-companion.mjs" cancel "$ARGUMENTS"`
