# Amnesiac Story OS (File-Backed Authoring Workflow)

This repository is a **local-first, file-backed story operating system** designed for an amnestic writing workflow.

You (human or AI collaborator) should treat this repository as a **procedure engine**, not a notes pile:

1. Record changes as events.
2. Regenerate state summaries from events.
3. Generate or update todos from playbook steps.
4. Move to the next explicit action.

If you do not know what to do next, follow **`playbooks/playbook_start_here.md`** exactly.

---

## Start Here (No Ambiguity)

### Step 1: Open the active queue
1. Read `todo/todo_master.md`.
2. Find the first task with status `NEXT` and no unmet dependency.
3. If no task qualifies, run the *Daily Triage* section in `playbooks/playbook_start_here.md`.

### Step 2: Execute the referenced playbook
1. Open the task's `origin_playbook` and `origin_step`.
2. Follow the playbook **step by step**.
3. Do not skip gates.

### Step 3: Write changes as durable records
1. Append narrative changes to chapter event logs (`chapters/*/events/*.ndjson`).
2. Update canon only through explicit decision records (`decisions/*.md`) when required.
3. Regenerate projections in `build/projections/`.

### Step 4: Update task graph
1. Mark completed tasks `DONE`.
2. Add child tasks created by your current playbook step.
3. Link each new task to a parent and dependency fields.

### Step 5: Stop condition
You are done only when:
- current task is `DONE`, and
- all mandatory child tasks are complete or explicitly deferred with rationale.

---

## Canonical Data Rules

- **Events are append-only.** Do not rewrite historical event lines unless fixing format corruption.
- **Summaries are derived.** `build/projections/*` can be regenerated.
- **Stable IDs are mandatory.** Use IDs like `char_0001`, `loc_0003`, `plot_0002`, `ch01_sc02`.
- **Every task needs provenance.** Include `origin_playbook` and `origin_step`.
- **Retcons require decision records.** Use `playbooks/playbook_retcon.md`.

---

## Repository Map

- `playbooks/`: executable procedures.
- `todo/`: task graph files.
- `canon/`: story bible and entity records.
- `chapters/`: chapter/scene outlines and event logs.
- `editor/`: feedback intake and resolution records.
- `build/projections/`: generated current-state summaries.
- `decisions/`: explicit canon/retcon decisions.
- `templates/`: templates for events, tasks, and records.

---

## Minimum Loop to Hand Off Drafting

Before chapter work, run a one-time foundation bootstrap if premise/purpose/themes/minimal cast are not yet canonical:

0. `playbook_story_foundation.md`

Run this loop per chapter until complete:

1. `playbook_chapter_outline.md`
2. `playbook_scene_outline.md` (for each scene)
3. `playbook_drafting.md`
4. `playbooks/playbook_chapter_lifecycle.md` (run lifecycle gates, then initialize next chapter)
5. `playbook_editor_intake.md` (when feedback arrives)
6. `playbook_retcon.md` (when continuity/canon issues appear)

When chapter gates pass, the package is handoff-ready for drafting and controlled next-chapter startup.
