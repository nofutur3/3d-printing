# 3D Printing

Designs for 3D printing — one directory per project under `projects/`, each with the source files, photos, build/print instructions, and (once published) a link to Printables.

Managed with the `3d-print-project` skill (`.claude/skills/3d-print-project/`) — scaffolds new projects, keeps this table in sync, drafts the Printables submission text, and can drive the actual Printables upload.

## Projects

| Project | Status | Printables |
| --- | --- | --- |
| [Microsoft Surface Arc // Lidl Parkside pegboard holder](projects/surface-arc-pegboard-holder/) | Published | [printables.com/model/1647465](https://www.printables.com/model/1647465-microsoft-surface-arc-lidl-parkside-pegboard-holde) |

## Layout

```
projects/
  <slug>/
    README.md                  - description, instructions, status
    printables-submission.md   - ready-to-paste Printables fields
    files/                     - STL/3MF/STEP
    images/                    - photos, renders
```
