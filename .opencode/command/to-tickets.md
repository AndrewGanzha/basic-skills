---
description: Break the spec into tracer-bullet tickets at .scratch/<feature>/issues/NN-slug.md
---

Break the spec, plan, or current conversation into **tickets**: tracer-bullet
vertical slices, each declaring the tickets that **block** it.

The tracker and layout are fixed in `AGENTS.md`: one file per ticket under
`.scratch/<feature-slug>/issues/<NN>-<slug>.md`, numbered from `01` in
dependency order (blockers first). If the feature slug is unclear, ask once.

## Process

### 1. Gather context

Work from the conversation. If the user passes a reference (spec path, feature
slug) as an argument, read it in full.

### 2. Explore the codebase (if not already done)

Ticket titles and descriptions must use the project's `GLOSSARY.md` vocabulary
and respect ADRs in the area you touch. Look for prefactors that would make the
implementation easier: "make the change easy, then make the easy change."

### 3. Draft vertical slices

<vertical-slice-rules>

- Each slice cuts a narrow but COMPLETE path through every layer (schema, API,
  UI, tests): vertical, NOT a horizontal slice of one layer.
- A completed slice is demoable or verifiable on its own.
- Each slice fits in a single fresh context window.
- Do any prefactoring first.

</vertical-slice-rules>

Give each ticket its **blocking edges**: the tickets that must complete before it
can start. A ticket with no blockers can start immediately.

**Wide refactors are the exception to vertical slicing.** A wide refactor is one
mechanical change whose blast radius fans across the whole codebase, so no single
vertical slice can land green. Sequence it as **expand–contract**: expand (add
the new form beside the old), then migrate call sites in batches each blocked by
the expand, then contract (delete the old form) blocked by every migrate batch.

### 4. Quiz the user

Present the breakdown as a numbered list. For each ticket show: **Title**,
**Blocked by**, and **What it delivers** (the end-to-end behaviour it makes
work). Ask whether the granularity is right, whether the blocking edges are
correct, and whether any ticket should be merged or split. Iterate until
approved.

### 5. Write the tickets

Write one file per approved ticket under `.scratch/<feature-slug>/issues/`,
numbered from `01` in dependency order, using the template below. Never write a
single combined file.

<local-ticket-template>

# <NN>: <Ticket title>

**What to build:** the end-to-end behaviour this ticket makes work, from the
user's perspective, not a layer-by-layer implementation list.

**Blocked by:** the numbers/titles of the tickets that gate this one, or
"None (can start immediately)".

**Status:** ready-for-agent

- [ ] Acceptance criterion 1
- [ ] Acceptance criterion 2

</local-ticket-template>

Avoid specific file paths or code snippets — they go stale fast. Exception: a
prototype snippet that encodes a decision more precisely than prose may be
inlined and noted as coming from a prototype.
