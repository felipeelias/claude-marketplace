---
name: address-comments
description: "Fetch, categorize, fix, and resolve all PR review comments (inline, reviews, nitpicks) from CodeRabbit, Copilot, and other reviewers"
user-invocable: true
allowed-tools: Bash(gh api:*), Bash(gh pr:*), Bash(gh repo:*), Bash(git add:*), Bash(git commit:*), Bash(git push:*), Bash(git diff:*), Bash(golangci-lint:*), Bash(go test:*), Bash(go build:*), Bash(PRE_COMMIT_ALLOW_NO_CONFIG:*), Read, Edit, Glob, Grep
---

## Context

- PR number: !`gh pr view --json number --jq .number`
- PR URL: !`gh pr view --json url --jq .url`
- Repo: !`gh repo view --json nameWithOwner --jq .nameWithOwner`
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

### 5. Reply and resolve threads

For each addressed thread, reply with a short comment explaining what was fixed and in which commit, then resolve the thread.

```sh
# Reply to inline comment
gh api repos/{REPO}/pulls/{PR}/comments/{COMMENT_ID}/replies -f body='Fixed in {SHA} — {what was done}.'

# Resolve the thread
gh api graphql -f query='mutation { resolveReviewThread(input: {threadId: "ID"}) { thread { isResolved } } }'
```
