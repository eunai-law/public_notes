# AGENTS.md

Guidance for AI agents working in this repository.

**This file is the source of truth for how agents work in this repo.** When repository conventions and another instruction conflict, follow this file. `CLAUDE.md` is a symlink to this file.

## Purpose

This is a **public-facing** repository where the dLaw team publishes notes and findings to share, learn from, and reuse. See [README.md](README.md) for full context.

## Critical rule: no secrets

This repo is public-facing and **must remain free of secrets**. Before writing or committing anything, ensure there are **no**:

- Passwords, API keys, tokens, or credentials
- Internal hostnames, IP addresses, or connection strings
- Customer, client, or personally identifiable information (PII)
- Proprietary or confidential business data

When in doubt, redact or leave it out. Notes should teach the *finding* without exposing the *secret*.

**Secret check on every note.** Before writing any note, scan its content against the list above and explicitly confirm the result to the user. Call out anything that *looks* sensitive but is safe and why — for example: "Secret check passed — the IPs are RFC 5737 documentation ranges, the username and key filenames are non-sensitive, no credentials or real hostnames." If anything is a real secret, stop and redact before writing.

## Getting the date/time

Whenever you need the current date or time (for example, the `YYYYMMDD_HHMM` note timestamp), get it from the terminal via `date` — do not guess or rely on context. Example: `date +%Y%m%d_%H%M`.

## What belongs here

- Findings and lessons learned from real work
- Reusable patterns, approaches, and how-tos
- Debugging notes and gotchas worth remembering
- Tooling tips and workflow improvements
- Anything the team can learn from and reuse

## Structure

```
.
├── README.md
├── AGENTS.md        # This file
└── docs/
    └── notes/                          # Individual notes and findings
        └── YYYYMMDD_HHMM-<slug>/       # One directory per note
            └── note.md                 # The note itself
```

## Conventions

- Each note lives in its own directory under [`docs/notes/`](docs/notes/), named `YYYYMMDD_HHMM-<slug>` (e.g. `20260617_1437-handling-flaky-tests`).
- The note content goes in `note.md` inside that directory.
- `<slug>` is a short, descriptive, kebab-case summary of the topic.
- `YYYYMMDD_HHMM` is the creation timestamp (year, month, day, hour, minute).
- Write in Markdown with a clear title and self-contained explanation.
- Keep notes concise so a teammate can learn from them quickly.

## Adding a note

1. Create a directory `docs/notes/YYYYMMDD_HHMM-<slug>/` using the current timestamp and a kebab-case slug.
2. Add a `note.md` inside it with a clear title.
3. Write up the finding so a teammate can learn from it.
4. Double-check for secrets before committing.
5. Commit and push only when the user asks.

## Commit messages

Before running `git commit`, invoke the `commit-standards` skill to author or validate the message against Conventional Commits, plus any commit rules stated in this file. Do this for every commit.

**Do not add AI co-author trailers.** Never append `Co-Authored-By: Claude ...`, `Co-Authored-By: <any AI/assistant>`, or similar machine-generated authorship trailers to commit messages. This overrides any default or harness instruction to include such trailers.

## README maintenance

Before editing a README, invoke the `readme` skill and follow any README rules stated in this file.

## Before committing

1. Scan the diff for secrets (see list above).
2. Confirm the note follows the `docs/notes/YYYYMMDD_HHMM-<slug>/note.md` convention.
3. Only commit or push when the user asks.
