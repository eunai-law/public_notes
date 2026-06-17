# Public Notes

[![Status](https://img.shields.io/badge/status-in%20development-yellow?style=flat-square)](#status)
[![Visibility](https://img.shields.io/badge/visibility-public-brightgreen?style=flat-square)](#)

Published notes and findings from the dLaw team — written to be shared, learned from, and reused.

## What this is

This repository is a place for the dLaw team to publish **notes and findings** that are useful to share across the team. Think of it as a growing knowledge base: things we figured out, patterns worth reusing, debugging war stories, tool tips, and lessons learned.

The goal is to capture knowledge so it doesn't stay locked in one person's head — so the next person who hits the same problem can learn from what we already worked out.

## What belongs here

- Findings and lessons learned from real work
- Reusable patterns, approaches, and how-tos
- Debugging notes and gotchas worth remembering
- Tooling tips and workflow improvements
- Anything the team can learn from and reuse

## What does NOT belong here

This repository is **public-facing and must be free of secrets**. Before committing, make sure notes contain **no**:

- Passwords, API keys, tokens, or credentials of any kind
- Internal hostnames, IP addresses, or connection strings
- Customer, client, or personally identifiable information (PII)
- Proprietary or confidential business data
- Anything you wouldn't want shared outside the team

When in doubt, leave it out or redact it. Write notes so they teach the *finding* without exposing the *secret*.

## Structure

```
.
├── README.md        # You are here
└── docs/
    └── notes/       # Individual notes and findings
```

- **`docs/notes/`** — Drop individual notes here, one topic per file. Use clear, descriptive filenames (e.g. `handling-flaky-tests.md`).

## Adding a note

1. Create a new Markdown file in [`docs/notes/`](docs/notes/).
2. Give it a descriptive filename and a clear title.
3. Write up the finding so a teammate can learn from it.
4. **Double-check for secrets** before committing.
5. Commit and push.

## Status

**In development.** This is a young, growing knowledge base — notes are added as the team finds things worth sharing. The repository is **public**, so everything here is intended to be safe to share openly and must remain free of secrets.

## Contributing

Everyone on the dLaw team is encouraged to contribute. Keep notes clear, concise, and secret-free. The more we share, the more we all learn.
