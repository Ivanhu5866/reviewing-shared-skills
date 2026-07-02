# Review: GitHub Issue Sync

## Verdict: NO-SHIP — hardcoded token, machine-specific path, and a description that summarizes the workflow.

## Blocking
- [Secrets] A real-looking token is hardcoded in the example (`TOKEN = "ghp_..."`).
  Remove it. Read from `GITHUB_TOKEN` env var or a config file; ship `.env.example`
  and add the secret file to `.gitignore`. Add setup steps for getting the token.
- [Portability] Output path `/home/alice/issues.json` is machine-specific. Write to
  the current working directory or a configurable path.
- [Frontmatter > name] `name: GitHub Issue Sync` has spaces/caps. Use
  `github-issue-sync`.

## High
- [Frontmatter > description] Description summarizes the workflow ("fetches…parses…
  writes…opens") and ends with "Run it whenever." Rewrite as triggers only, e.g.
  "Use when you need GitHub issues available offline or mirrored to a local file."
- [Portability] Repo `acme/widgets` is hardcoded. Make owner/repo parameters.
- [Structure] No "When to Use" / "not for" section. Add one.

## Nice-to-have
- [Time-sensitive] "As of June 2026 … current v3 API" will rot. Drop the date.
- [Examples] Example has no error handling and no comments explaining WHY.
- [Keywords] Add searchable terms: "offline issues", "mirror", "export issues".

## Passed
- Has a concrete, runnable example (just unsafe).
- Overview states what it does in one sentence.
- Single language, not a fill-in template.
