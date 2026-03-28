# PR Description Format

Apply when writing pull request descriptions.

## Structure

### Title

Commit subject line, or the most recent commit if updating an existing PR.

### Body

1. **Summary** (H2): one or two sentences describing the purpose. Focus on why.
2. **Why** (H2): lead with the conclusion (main reason), then support with details. Most important reason first, supporting context after. Cover business/technical reason, problem being solved, relevant context.
3. **What** (H2): bullet points of changes. Keep it simple.

### Optional Sections

Include when relevant. Each is an H3 section appended after **What**.

**Parent PR:** when the PR is stacked, find the parent PR URL and add:

```markdown
### Parent PR

- <url>
```

## Style

- Present tense: "Remove" not "Removes"
- Use `code formatting` for technical terms
- Avoid vague descriptions, implementation details, or repeating the title

## Example

```markdown
## Summary

Remove the deprecated `logMode` function and simplify persistent logger configuration.

## Why

The `logMode` function was deprecated, making the mode parameter unnecessary.

## What

- Remove `logMode` function from run-mode configuration
- Remove `mode` parameter from persistent logger methods
```
