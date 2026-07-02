# Skill Review Checklist

Score each item Pass / Fail / Warn with evidence. Sources: superpowers
`writing-skills`, anthropic skill best-practices, plus practical "common sense"
rules. Mechanical items are Blocking; judgment items are usually High/Nice.

## 1. Frontmatter (Blocking)
- [ ] `name` present, letters/numbers/hyphens only, verb-first or gerund.
- [ ] `description` present, third person, starts with "Use when…", triggers only.
- [ ] description does NOT summarize the workflow (agents skip body if it does).
- [ ] total frontmatter < 1024 chars (HARD limit — over this can break loading).
- [ ] keywords a searcher would use (symptoms, errors, tools, synonyms) included.

## 2. Structure
- [ ] Overview: what it is + core principle in 1-2 sentences.
- [ ] When to Use, with symptoms AND a "not for" list.
- [ ] Sections scaled to complexity; no filler. Tables/lists for reference.
- [ ] Heavy reference (100+ lines) or reusable tools moved to separate files.
- [ ] Flowcharts only for non-obvious decisions, not for linear/reference content.

## 3. Examples (Blocking if absent)
- [ ] At least one complete, runnable, real example.
- [ ] Not a fill-in-the-blank template; not duplicated across 5 languages.
- [ ] Comments explain WHY, not the obvious.

## 4. Token efficiency
- [ ] Concise; cross-references instead of repeating other skills.
- [ ] Progressive disclosure; references not deeply nested (one hop from SKILL.md).
- [ ] No time-sensitive content ("current", dated). Consistent terminology.
- [ ] Assumes a smart agent: no paragraphs re-explaining what any agent knows
      (e.g. "PDFs are a file format…"). Each paragraph justifies its token cost.

## 5. Degrees of freedom
- [ ] Specificity matches task fragility:
      - High freedom (text steps) when many approaches are valid.
      - Medium freedom (parameterized pseudocode/script) when a pattern exists.
      - Low freedom ("run exactly this; don't add flags") when fragile/sequential.
- [ ] Fragile/destructive sequences are NOT left to agent improvisation.

## 6. Cross-references
- [ ] Other skills referenced by name with explicit markers
      (e.g. **REQUIRED:** Use `other-skill`), not vague "see …".
- [ ] No `@file` links that force-load files and burn context.

## 7. Testing evidence
- [ ] Author shows the skill was actually exercised, not just written.
- [ ] For discipline/rule skills: baseline (fails without skill) + with-skill pass.
- [ ] Bundled scripts/commands are runnable as written.

## 8. License & attribution
- [ ] If shared publicly, a `license` (and attribution if adapted) is present.

## 9. Secrets & config (Blocking)
- [ ] No hardcoded tokens, keys, passwords, or personal emails.
- [ ] If OAuth/API tokens needed: use env vars or a config file.
- [ ] `.env.example` / `config.*.template` shipped; secrets in `.gitignore`.
- [ ] Setup documented in `SKILL.md` OR `README.md`: how to create the config
      from the template, where to obtain credentials, and a "do not commit" note.
- [ ] If a config template ships, its setup steps actually exist somewhere (a
      template with no documented setup flow is an incomplete pass).

## 10. Portability & generality
- [ ] No hardcoded user-specific paths (e.g. /home/alice/...); use cwd or vars.
- [ ] Runtime/OS-agnostic where reasonable; deps declared with install steps.
- [ ] Works for others, not just the author's machine.

## 11. Safety
- [ ] Re-runnable / idempotent where it matters.
- [ ] No destructive actions (delete, force-push, prod writes) without confirmation.
- [ ] Privacy: no sensitive data sent to third parties.

## 12. Cross-runtime portability
Static checks flag risk; the only real proof is running the skill on each target
runtime/model (Claude, Gemini, Copilot, …) — see note below.
- [ ] Speaks in actions ("read the file", "dispatch a subagent", "create a todo"),
      NOT a runtime's tool name (`view`, `apply_patch`, `read_file`, `task`).
- [ ] No hardcoded skills path; uses the `~/.agents/skills/` alias or stays generic
      (not `~/.claude/skills` or `~/.copilot/skills` only).
- [ ] No hardcoded instructions file; says "your instructions file" (not `CLAUDE.md`,
      `AGENTS.md`, or `GEMINI.md` exclusively).
- [ ] Other skills referenced by name, not `@file` force-load or one runtime's
      invoke syntax.
- [ ] Frontmatter sticks to `name`/`description` (+ agentskills.io spec fields); no
      runtime-only fields relied on.
- [ ] OS/shell/lang assumptions declared (avoids bash-only, GNU-only flags, assumes
      python3/node without saying so).
- [ ] Guidance not over/under-tuned to one model ("test with all models you plan
      to use").

**Real proof = run it.** Static review cannot confirm portability. Exercise the
skill (subagent baseline + with-skill) on each runtime/model you intend to support.

## Priority mapping
- Blocking: frontmatter invalid, no example, hardcoded secrets, destructive default,
  fragile sequence left to improvisation (wrong degrees of freedom), a hardcoded
  runtime tool/path that breaks the skill on other runtimes.
- High: workflow-summary description, missing "not for", poor portability,
  no testing evidence, `@file` force-loading cross-references, runtime-specific
  assumptions (tool names, instructions file, skills path).
- Nice-to-have: keyword gaps, verbose sections, naming polish, missing license.
