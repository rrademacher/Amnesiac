# Playbook: Chapter Outline

## Purpose
Produce or revise a chapter outline that is canon-safe, event-capturable, and ready for scene-level decomposition.

## Entry conditions
- Story foundation bootstrap is complete (premise, purpose, themes, and minimal cast are canonical).
- Target chapter exists under `chapters/ch##/`.
- `todo/active_task.md` references this chapter.
- Required context files are readable.

## Steps

### CO-01 — Preflight anchor
1. Read target chapter outline file (`chapters/ch##/ch##_outline.md`) if present.
2. Read relevant entities and active plot files:
   - `canon/story_bible.md`
   - `canon/entities/` records when IDs already exist
   - `build/projections/plot_status.md`
3. Read unresolved foreshadowing debt from `todo/todo_master.md` (tasks tagged in title or context as "foreshadowing"). If none exist, record "none" in working notes.
4. Write a one-paragraph `Chapter Purpose` statement.

### CO-02 — Build beat skeleton
For each beat, specify:
1. beat ID
2. goal
3. conflict/opposition
4. outcome
5. affected plot IDs

### CO-03 — Create required scene placeholders
1. Create or update `chapters/ch##/scenes/ch##_sc##.md` files for each planned scene.
2. Add TODO markers for missing details.

### CO-04 — Capture events
1. Append chapter-level events to `chapters/ch##/events/ch##_events.ndjson`.
2. Ensure each event contains IDs for involved entities and scope.

### CO-05 — Trigger projection and task cascade
1. Update `build/projections/plot_status.md` and related projections.
2. Spawn tasks for:
   - unresolved canon constraints
   - foreshadowing debt introduced
   - missing entity updates when new IDs appear in events without a corresponding `canon/entities/*` record

## Required outputs
- Chapter outline includes purpose + beats.
- Event log appended.
- Child tasks generated with dependencies.

## Exit gate
- Outline task can be marked `DONE` only if all required scene placeholder tasks exist and no blocking continuity issue is unresolved.

## Failure handling
- If canon conflict appears, stop and invoke `playbook_retcon.md` before continuing.
