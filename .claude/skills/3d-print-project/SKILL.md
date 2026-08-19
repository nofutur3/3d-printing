---
name: 3d-print-project
description: |
  Manage this repo's 3D-printing projects: scaffold a new project directory,
  keep the root README's project table in sync, draft a Printables-ready
  submission (title/summary/tags/print-settings/description) from project
  notes, and optionally drive the actual Printables upload via browser
  automation. Use when the user wants to start a new print project, prepare
  one for publishing, or update an already-published listing.
---

# 3D Print Project

This repo holds one directory per design under `projects/<slug>/`, each with its
own `README.md` (description + instructions), `printables-submission.md`
(the publish-ready fields), `files/` (STL/3MF/STEP), and `images/` (photos,
renders). `projects/_template/` is the scaffold source. The root `README.md`
has a table listing every project — keep it in sync whenever a project is
added or its status changes.

## Task: scaffold a new project

1. Ask for (or infer from context) a short name; derive a kebab-case slug.
2. Copy `projects/_template/` to `projects/<slug>/`, including the empty
   `files/`/`images/` dirs.
3. Fill in `README.md`'s title and whatever description/instructions the user
   already gave you — leave placeholders for what you don't know yet, don't
   invent print settings or specs.
4. Add a row to the root `README.md` table, status "In progress", Printables
   column "—".

## Task: draft the Printables submission

Given a project's `README.md` (and any extra notes/photos/print-settings the
user shares), fill in `printables-submission.md`:

- **title/summary**: summary is one sentence, shown right under the title on
  Printables — don't just repeat the title.
- **category**: suggest the closest match; if unsure, ask rather than
  guessing — wrong category placement hurts discoverability.
- **print_settings**: only fill in what's actually known (from the user, or
  from slicer output they share). Leave blank rather than guessing values
  that affect whether someone else's print succeeds.
- **license**: default `CC BY-NC 4.0` unless the user says otherwise, or
  unless this is a remix — remixes should generally match the original's
  license terms (check `remix_of.license`).
- **description**: write the full body, then run it (and the summary) through
  the `humanizer` skill before considering it done. This applies to every
  piece of text destined for Printables — it's public-facing and shouldn't
  read like an AI wrote it.

Update the root README's status to "Ready to publish" when this is done.

## Task: publish (or update) on Printables

Printables sits behind Cloudflare bot-detection and requires the user's own
logged-in session — use the browser tools against the user's existing Chrome
profile, don't attempt login or enter credentials.

1. Confirm `printables-submission.md` is complete and humanized first.
2. Navigate to the upload/edit flow, fill in title, summary, category, tags,
   description, print settings, license, and upload the files from `files/`
   and `images/`.
3. **Stop before the final Publish/Save button.** Show the user a summary of
   what's about to go live and get explicit confirmation — this is public,
   irreversible-feeling content on their account, not a draft.
4. Once confirmed and published, capture the resulting URL: write it into
   `printables_url` in `printables-submission.md`, the project `README.md`'s
   status section, and the root README table's Printables column and status
   ("Published").

If editing an already-published listing instead, same flow, just via
Printables' edit page instead of upload — and skip step 4's URL capture since
it's already set.
