# Design Skills

How the graphic-design capability is wired, and the standing reminder to use it.

## The one entry point

`graphic-design` is the **only** design skill in the index
(`~/.hermes/skills/design/graphic-design/`). Everything else is a library behind it.

```
design/
├── graphic-design/            ← the only indexed skill
│   ├── SKILL.md               pre-flight + build method + guardrails
│   └── references/library.md  220 skills, grouped, with paths
├── .archive/                  ← 220 vendored skills, live but unindexed
├── env.sh                     source before running any library script
├── ATTRIBUTION.md  README.md  install-from-source.py
```

## Why `.archive`

`.archive` is one of Hermes' `EXCLUDED_SKILL_DIRS` in `agent/skill_utils.py`, so the skill
scanner prunes the whole directory. The 220 skills therefore cost **zero prompt tokens** and
appear nowhere in the skill index, while every file stays live and readable.

This took the design repertoire from 221 index entries (~6.5k tokens every turn) to **1 entry
(~60 characters)**.

Trade-off: archived skills are **not** loadable via `skill_view` — read them by path with
`read_file` instead. Their `scripts/`, `assets/` and `references/` work as shipped.

To promote one back to a first-class skill, move it out of `.archive/`.

## The reminder rule

Memory carries a standing entry so this fires reliably:

> Visual work: load skill `graphic-design` first (it runs the taste + anti-slop pre-flight
> before any code, and carries a 220-skill art/design library). Fires for anything that gets
> looked at, not just explicit "design" asks — decks/slides, thumbnails, charts and data-viz,
> posters/print, logos/wordmarks, icon sets, any UI or landing page, diagrams, social images.

The broad trigger list is the point. The failure mode isn't forgetting design requests — it's
not *recognising* that a deck, a thumbnail, a chart or a diagram is a design job.

## Do not use `skills.auto_load` for this

`skills.auto_load` in `config.yaml` renders a skill's **full content** into every new session
with an IMPORTANT banner. Pinning `graphic-design` that way would cost ~2k tokens on every
session, including entirely non-visual ones. Memory is the cheaper, better-targeted channel —
it's injected every turn and the trigger is conditional on the task.

Revisit only if the reminder proves unreliable.

## The pre-flight

The skill's order is deliberate: prevention before code, not audit after.

1. Read `.archive/mengto/no-ai-design-slop/SKILL.md` — the ruleset, loaded as constraints
   going in rather than a checklist at the end.
2. Read `.archive/tastemaker/tastemaker/SKILL.md` — the taste engine. Decides palette, type
   pairing, spacing rhythm and radius/shadow language *before* any markup exists, and extracts
   real tokens from reference images instead of describing a vibe in text.
3. State the visual thesis in one line.

Hard gate: no markup, CSS, JSX or SVG until that's done. `audit-ai-design-slop` stays for the
post-build critique.

## Running library scripts

```bash
source ~/.hermes/skills/design/env.sh
```

Python venv at `/home/ubuntu/.venvs/design` (uv, 3.12); Node + `playwright-core` global with
Chromium in `~/.cache/ms-playwright`; `poppler-utils` system. The env script clears an
inherited `PYTHONPATH`, which otherwise leaks Hermes' python3.14 site-packages into the 3.12
venv and breaks numpy.

`node: command not found` or `Cannot find module 'playwright-core'` means `env.sh` wasn't
sourced — that's the usual cause, not a broken skill.

## Provenance

Eight MIT-licensed public collections, vendored unmodified apart from frontmatter
normalisation: MengTo (147), Owl-Listener designer-skills (34), Emil Kowalski (16), Jakub
Krehel (9), ComposioHQ (5), ConardLi garden-skills (5), elayadesign (2), codeswithroh
tastemaker (2). Full list in `ATTRIBUTION.md`.
