# Playbook: Start Here (Daily Control Loop)

## Purpose
Use this playbook whenever you start a session or lose context. It re-anchors you to canon, active goals, and the next unambiguous action.

## Entry conditions
- Repository is available locally.
- You can read and edit files.

## Steps

### SH-01 — Load control context
1. Read `todo/todo_master.md`.
2. Read `canon/story_bible.md`.
3. Read `editor/notes_inbox.md`.
4. Read `build/projections/continuity_report.md`.

### SH-02 — Select the next executable task
1. Find tasks marked `NEXT`.
2. Exclude any task with unmet `depends_on` entries.
3. If multiple remain, pick lowest `priority` number.
4. Write the selected task ID into `todo/active_task.md`.

### SH-03 — If no executable task exists (Daily Triage)
1. Create a new triage task in `todo/todo_master.md` as `NEXT`.
2. Run these checks in order:
   - unresolved editor notes
   - unresolved continuity conflicts
   - chapters with missing outline
   - chapters with outline but no scene files
3. Generate at least one executable child task with explicit provenance.

### SH-04 — Execute selected task playbook
1. Open the task's `origin_playbook` and `origin_step`.
2. Perform only the specified procedure.
3. Update task status and spawn child tasks as required.

## Required outputs
- `todo/active_task.md` updated.
- At least one executable `NEXT` task exists.

## Exit gate
- You can answer both questions from files alone:
  1. "What am I doing now?"
  2. "What do I do immediately after this?"

## Failure handling
- If dependencies are cyclic, create `task_cycle_breaker` task, mark blockers, and record rationale in `decisions/`.
