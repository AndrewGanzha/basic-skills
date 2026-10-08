---
description: Implement a spec or ticket test-first, then review before committing
---

Implement the work described by the user in the spec or tickets.

If the user passes a ticket reference, read it from
`.scratch/<feature-slug>/issues/` (or the spec at `.scratch/<feature-slug>/spec.md`)
and state its title before starting. If the reference is ambiguous, ask.

Call the skill tool with "tdd" where possible, at pre-agreed seams.

Run typechecking regularly, single test files regularly, and the full test suite
once at the end.

Once done, call the skill tool with "code-review" to review the work.

Commit your work to the current branch.
