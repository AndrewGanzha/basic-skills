---
description: Synthesize the current conversation into a spec at .scratch/<feature>/spec.md
---

Turn the current conversation and codebase understanding into a spec. Do NOT
interview the user again — synthesize what you already know.

The feature slug and file layout are fixed in `AGENTS.md`: write the spec to
`.scratch/<feature-slug>/spec.md`. If the feature slug is not obvious from the
conversation, ask for it once.

## Process

1. Explore the repo if you haven't already. Use the project's `GLOSSARY.md`
   vocabulary throughout the spec and respect any ADRs in the area you touch.

2. Sketch the seams at which you will test the feature. Prefer existing seams,
   and the highest seam possible. Propose new seams only if necessary, at the
   highest point you can. Fewer seams is better; the ideal is one.

3. Check with the user that these seams match their expectations.

4. Write the spec using the template below to
   `.scratch/<feature-slug>/spec.md`.

<spec-template>

## Problem Statement

The problem the user is facing, from the user's perspective.

## Solution

The solution, from the user's perspective.

## User Stories

A long, numbered list, each in the form:

1. As an <actor>, I want a <feature>, so that <benefit>

Cover all aspects of the feature.

## Implementation Decisions

Modules to build/modify, their interfaces, technical clarifications,
architectural decisions, schema changes, API contracts, specific interactions.

Do NOT include specific file paths or code snippets — they go stale fast.
Exception: a prototype snippet that encodes a decision more precisely than prose
(state machine, reducer, schema, type shape) may be inlined, trimmed to the
decision-rich parts and noted as coming from a prototype.

## Testing Decisions

What makes a good test here (external behavior only, not implementation
details), which modules are tested, and prior art for those tests.

## Out of Scope

What this spec deliberately excludes.

## Further Notes

Anything else.

</spec-template>
