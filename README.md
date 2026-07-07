# reviewing-shared-skills

An agent skill for reviewing another skill before it is shared — its job is to
**find the things worth fixing** so the skill is ready to share.

It checks a candidate skill against general skill-authoring standards (superpowers
`writing-skills` + Anthropic best-practices) plus common-sense practical rules, then
produces a written report: prioritized fixes (Blocking / High / Nice-to-have) and a
ship / no-ship verdict. It surfaces problems only — the author fixes them; this
skill does not rewrite their skill. For any skill author, not a specific team.

## Contents

```
SKILL.md                            # workflow + report format + key rules
references/skill-rules-checklist.md # 12 rule categories, Pass/Fail/Warn
examples/
  sample-skill-SKILL.md             # a flawed candidate skill
  sample-review-report.md           # its completed review
```

## What it checks

1. Frontmatter (name, description triggers-only, no workflow summary)
2. Structure (Overview, When to Use / not for, progressive disclosure)
3. Examples (at least one complete, runnable, real example)
4. Token efficiency
5. Degrees of freedom
6. Cross-references
7. Testing evidence
8. License & attribution
9. Secrets & config (no hardcoded tokens; env vars / config file + setup docs)
10. Portability & generality
11. Safety
12. Cross-runtime portability (Claude, Gemini, Copilot)

## Installation

Copy or symlink this directory into your runtime's skills directory, e.g.:

```bash
ln -s "$(pwd)" ~/.copilot/skills/reviewing-shared-skills
```

## License

MIT
