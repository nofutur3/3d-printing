# CLAUDE.md

Guidance for Claude Code working in this repository. See `README.md` for what this repo is to a human reader.

## Layout

```
projects/
  <slug>/
    README.md                  - description, instructions, status
    printables-submission.md   - ready-to-paste Printables fields
    files/                     - STL/3MF/STEP
    images/                    - photos, renders
```

`projects/_template/` is the scaffold source for new projects.

## Managing projects

Use the `3d-print-project` skill (`.claude/skills/3d-print-project/SKILL.md`) for all of: scaffolding a new project, keeping the root `README.md`'s project table in sync, drafting `printables-submission.md`, and (with explicit confirmation before anything goes live) driving the actual Printables upload via browser.

Any text destined for Printables (title, summary, description) should be run through the `humanizer` skill (`.claude/skills/humanizer/`, a submodule) before being treated as final — it's public-facing.
