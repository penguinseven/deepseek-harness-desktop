# Issue tracker: GitHub

Issues and specs for this repository live in GitHub Issues for `penguinseven/deepseek-harness-desktop`. Use the `gh` CLI for issue operations.

## Conventions

- **Create an issue**: `gh issue create --title "..." --body "..."`.
- **Read an issue**: `gh issue view <number> --comments`, including labels and comments.
- **List issues**: `gh issue list --state open` with appropriate label and state filters.
- **Comment on an issue**: `gh issue comment <number> --body "..."`.
- **Apply or remove labels**: `gh issue edit <number> --add-label "..."` / `--remove-label "..."`.
- **Close**: `gh issue close <number> --comment "..."`.

The `github` remote is the product repository for this branch. The `origin` remote points to the upstream project and is not the issue-tracker target for this setup.

## Pull requests as a triage surface

**PRs as a request surface: no.** External pull requests are not included in ordinary triage discovery. Explicitly named pull requests may still be inspected when requested.

## When a skill says "publish to the issue tracker"

Create or update a GitHub issue in `penguinseven/deepseek-harness-desktop`.

## When a skill says "fetch the relevant ticket"

Run `gh issue view <number> --comments` from this repository.

## Wayfinding operations

The wayfinding map is a single GitHub issue labelled `wayfinder:map`; child work is represented by GitHub sub-issues when available. If sub-issues are unavailable, add a `Part of #<map>` line to the child issue body. Use `wayfinder:research`, `wayfinder:prototype`, `wayfinder:grilling`, or `wayfinder:task` for child issue types.

Native GitHub issue dependencies are the canonical blocking representation. When dependencies are unavailable, record `Blocked by: #<n>` in the child issue body. The frontier is the first open, unassigned child without an open blocker.
