---
name: web-design-guidelines
description: Review UI code for Web Interface Guidelines compliance. Use when asked to "review my UI", "check accessibility", "audit design", "review UX", or "check my site against best practices".
argument-hint: <file-or-pattern>
---

# Web Interface Guidelines

Review files for compliance with the rules in `rules.md` next to this file.

`rules.md` is a pinned copy of `command.md` from vercel-labs/web-interface-guidelines
(commit e3d624b, MIT, see `LICENSE`). Read it from disk; do not fetch a newer version from the
web. Updating it is a deliberate change made in its own commit.

## How it works

1. Read `rules.md`.
2. Read the specified files, or ask which files to review if none were given.
3. Check them against every rule that applies to the stack. Skip rules written for React or
   forms when the files have neither.
4. Report findings in the terse `file:line` format that `rules.md` describes.

## In this repository

`CLAUDE.md` wins where a rule conflicts with it. Report the conflict as a conflict, not as a
finding to fix. Known ones: headings and buttons stay in sentence case (not Title Case), and
`preconnect` does not apply because the site loads nothing from another domain.
