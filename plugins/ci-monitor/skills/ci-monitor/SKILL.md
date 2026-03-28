---
name: ci-monitor
description: "This skill should be used when the user asks to watch CI, monitor CI, check CI status, or wait for checks to finish on a PR or branch"
user-invocable: true
allowed-tools: Bash(git branch:*), Bash(gh pr checks:*), Bash(gh pr view:*), Bash(gh run list:*), Bash(gh run watch:*), Bash(gh run view:*)
---

## Context

- Has PR: !`gh pr view --json url --jq .url 2>/dev/null`
- Current branch: !`git branch --show-current`

## Steps

All watch commands MUST use `run_in_background: true`.

1. **If there's a PR:** run `gh pr checks --watch` with `run_in_background: true`
2. **If no PR:** find the latest run on the current branch:
   - `gh run list --branch <branch> --limit 1 --json databaseId --jq '.[0].databaseId'`
   - Then `gh run watch <RUN_ID> --exit-status` with `run_in_background: true`
3. Tell user: "CI monitoring started. You'll get a notification when it completes."
