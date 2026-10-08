# opencode — my engineering flow

A project-scoped [opencode](https://opencode.ai) config for a spec-driven,
test-first workflow. Five commands, hard-coded file architecture, no setup
interview.

Adapted from [mattpocock/skills](https://github.com/mattpocock/skills), rewritten
for opencode (commands for user-invoked steps, skills for the model-invoked
primitives) with the doc layout pinned in `AGENTS.md`.

## The flow

1. `/grill-with-docs` — relentless interview to align on the change, growing
   `GLOSSARY.md` and ADRs as decisions crystallise.
2. `/to-spec` — synthesize the conversation into `.scratch/<feature>/spec.md`.
3. `/to-tickets` — break the spec into tracer-bullet tickets.
4. `/implement` — build a ticket test-first, then review before committing.
5. `/review` — two-axis review (Standards + Spec) of the diff since a fixed point.

`/implement` and `/review` both drive the `code-review` skill; the doc-building
steps drive `grilling`, `domain-modeling`, and `tdd`.

## Install

Two layers, two mechanisms.

### Full flow (commands + skills) — clone

Clone the repo and copy the pieces into your project root, then restart opencode.

```bash
git clone <this-repo> /tmp/flow
cp -R /tmp/flow/.opencode /tmp/flow/skills /tmp/flow/AGENTS.md /tmp/flow/opencode.json /path/to/your-project/
```

The project `opencode.json` sets `"skills": { "paths": ["skills"] }`, so opencode
loads the skills straight from `skills/`.

Global alternative (available in every project):

```bash
cp -R .opencode/command/* ~/.config/opencode/command/
cp -R skills/*           ~/.config/opencode/skills/
```

### Skills only — `skills` CLI

The skills follow the [Agent Skills spec](https://agentskills.io), so the
[skills](https://skills.sh) CLI can install just them into opencode (project
`.agents/skills/`, global `~/.config/opencode/skills/`):

```bash
npx skills add <owner>/<repo> -a opencode
```

This installs `SKILL.md` files only — it does **not** install the commands or
`AGENTS.md`. Use the clone path for the full flow.

opencode reads config once at startup — **quit and restart** after installing.

## Where files go (fixed)

```
<repo>/
├── AGENTS.md                 # the pinned architecture
├── GLOSSARY.md               # domain language
├── docs/adr/NNNN-slug.md     # architecture decision records
└── .scratch/<feature>/
    ├── spec.md
    └── issues/NN-slug.md     # one ticket per file
```

## Layout

```
opencode.json                 # instructions: AGENTS.md; skills.paths: ["skills"]
AGENTS.md                     # hard-coded architecture (replaces the setup skill)
skills/                       # model-invoked primitives (installable via npx skills)
├── grilling/
├── domain-modeling/
├── tdd/
├── codebase-design/
└── code-review/
.opencode/
└── command/                  # user-invoked steps
    ├── grill-with-docs.md
    ├── to-spec.md
    ├── to-tickets.md
    ├── implement.md
    └── review.md
```

## Credits

Skills adapted from [mattpocock/skills](https://github.com/mattpocock/skills) (MIT).
