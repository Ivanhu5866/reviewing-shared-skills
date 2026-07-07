---
name: reviewing-shared-skills
description: Use when reviewing a skill an author wants to share before it is published or merged, when checking a SKILL.md against authoring standards, or when asked to vet a skill for missing examples, hardcoded secrets, or weak descriptions.
license: MIT
---

# Reviewing Shared Skills

## Overview

Review a candidate skill before it is shared with others. Check it against
general skill-authoring standards plus common-sense practical requirements, then
hand back a written report: prioritized fixes (Blocking/High/Nice-to-have) plus a
ship/no-ship verdict. The author fixes the issues; this skill does not rewrite
their skill.

This complements `writing-skills` (how to build a skill) by being the gate (is it
good enough to share). It is for any skill author, not one team.

## When to Use

- Someone submits a skill to share, publish, or merge.
- You are asked to vet, audit, or sign off on a SKILL.md.
- A skill "doesn't activate" or feels low quality and needs a structured check.

Not for: writing a skill from scratch (**Use `writing-skills`** instead), or
fixing the candidate yourself. This is review-only.

## Workflow

1. **Locate** the candidate skill directory. Read `SKILL.md`, `README.md` (setup
   often lives here, not in SKILL.md), and every bundled file (references, scripts,
   examples, config templates, `.env.example`, `.gitignore`).
2. **Score** each rule in `references/skill-rules-checklist.md` as Pass / Fail /
   Warn, with a one-line evidence note (quote or file:line).
3. **Prioritize** fixes: Blocking (must fix before sharing) > High > Nice-to-have.
4. **Report** using the format below. End with a one-line ship / no-ship verdict.

## Report Format

```
# Review: <skill-name>

## Verdict: SHIP / NO-SHIP — one sentence why

## Blocking
- [rule] problem — fix

## High
- [rule] problem — fix

## Nice-to-have
- [rule] problem — fix
```

Keep notes terse. Tie every issue to a checklist rule and a concrete fix. Do not
pad with praise.

## Key Rules (full list in references/skill-rules-checklist.md)

- **Frontmatter:** `name` hyphenated; `description` is third-person "Use when…"
  triggers only, NOT a workflow summary; under 1024 chars total.
- **Examples:** at least one complete, runnable, real example — not a fill-in
  template, not five languages.
- **Secrets:** never hardcode tokens/keys. If OAuth/API access is needed, require
  env vars or a config file, ship `.env.example`, and `.gitignore` the secrets.
- **Portability:** no hardcoded user paths, personal identity (author/committer/
  email/username), or fixed model names in scripts or example blocks; use
  placeholders or read at runtime. Runtime-agnostic where reasonable.
- **Degrees of freedom:** specificity matches fragility — low freedom ("run exactly
  this") for fragile/sequential steps, high freedom (text) for open-ended ones.
- **Cross-references:** name other skills with `REQUIRED`-style markers; never use
  `@file` links that force-load and burn context.
- **Common sense:** declared deps/setup, safe re-runs, no destructive action
  without confirmation, no time-sensitive content, license if shared publicly.
- **Cross-runtime portability:** speaks in actions not a runtime's tool names; no
  hardcoded skills path / instructions file; works on Claude, Gemini, Copilot.
  Static review flags risk — real proof is running it on each target runtime.

See `examples/` for a flawed sample skill and its completed review.
