# Project workflow

These conventions are fixed. Do NOT run a setup interview and do NOT ask where
files should go — read this file and follow it. The same layout applies to every
repo that uses this config.

## Issue tracker: local markdown

There is no remote tracker. Issues are markdown files inside the repo:

- The current feature is identified by a short kebab-case `<feature-slug>`.
- The spec lives at `.scratch/<feature-slug>/spec.md`.
- Tickets live at `.scratch/<feature-slug>/issues/<NN>-<slug>.md`.
  - Number from `01` in dependency order (blockers first).
  - One ticket per file. NEVER combine tickets into a single file.

## Triage vocabulary

Status is written inside each ticket as `**Status:** <label>`. Use only:

- `ready-for-agent` — an agent can pick it up
- `ready-for-human` — needs a human decision
- `needs-info` — blocked on missing information
- `wontfix` — deliberately not doing it

New tickets produced by `/to-tickets` start as `ready-for-agent`.

## Domain docs

- Glossary: `GLOSSARY.md` at the repo root.
- ADRs: `docs/adr/NNNN-slug.md`, sequential numbering from `0001`.
- Create the glossary, the ADR directory, or any file lazily — only when there
  is something real to write.

## The flow

Run the steps in order; each one is a command.

1. `/grill-with-docs` — relentless interview to align on the change. Grows
   `GLOSSARY.md` and ADRs as decisions crystallise.
2. `/to-spec` — synthesize what was discussed into `.scratch/<feature>/spec.md`.
3. `/to-tickets` — break the spec into tracer-bullet tickets under
   `.scratch/<feature>/issues/`.
4. `/implement` — build a ticket test-first, then review before committing.
5. `/review` — two-axis review (Standards + Spec) of the diff since a fixed point.
