---
name: address-comments
description: "Fetch, categorize, fix, and resolve all PR review comments (inline, reviews, nitpicks) from CodeRabbit, Copilot, and other reviewers"
user-invocable: true
allowed-tools: Bash(gh *), Bash(git *), Bash(PRE_COMMIT_ALLOW_NO_CONFIG*), Read, Edit, Glob, Grep
---

## Context

- PR: !`gh pr view --json number,url --jq '"\(.number) \(.url)"' 2>/dev/null || echo "no PR"`
- Repo: !`gh repo view --json nameWithOwner --jq .nameWithOwner 2>/dev/null || true`
- Branch: !`git branch --show-current`

## Steps

### 1. Fetch all comments

Run in parallel, using the repo and PR number from context:

- `gh api repos/{REPO}/pulls/{PR}/comments` — inline review comments
- `gh api repos/{REPO}/pulls/{PR}/reviews` — review bodies (contain nitpicks and summaries)

### 2. Categorize and present

Show the user a table:

| # | Source | File | Status | Issue |
|---|--------|------|--------|-------|

Statuses: **Already fixed**, **Actionable**, **Skip** (with reason).

Wait for user confirmation before proceeding.

### 3. Fix actionable items

Read each file, make the fix, verify it addresses the comment.

### 4. Validate, commit, push

Run the project's linter and tests before committing. Commit with `fix: address review feedback (...)`. Push to the PR branch.

### 5. Resolve threads

Fetch unresolved thread IDs with GraphQL, then resolve each addressed thread:

```sh
gh api graphql -f query='mutation { resolveReviewThread(input: {threadId: "ID"}) { thread { isResolved } } }'
```
