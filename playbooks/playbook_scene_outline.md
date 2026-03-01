# Playbook: Scene Outline

## Purpose
Turn a planned chapter beat into an executable scene outline with clear dramatic function and machine-readable event capture.

## Entry conditions
- Parent chapter outline exists.
- Scene task is active in `todo/active_task.md`.

## Steps

### SO-01 — Scene frame
Fill these fields in `chapters/ch##/scenes/ch##_sc##.md`:
1. POV
2. location ID
3. objective
4. opposition
5. outcome
6. links to parent beat ID

### SO-02 — Continuity check before writing events
1. Read relevant entity files.
2. Read recent chapter events.
3. Confirm no contradiction with first-known facts or timeline constraints.

### SO-03 — Event capture
1. Append scene events to chapter event log.
2. Mark uncertainty with `confidence: low` if needed.
3. If uncertainty affects canon, spawn a decision task.

### SO-04 — Spawn dependent tasks
Create children for:
- entity detail updates
- foreshadowing insertion in earlier chapter (if required)
- editor clarification if scene conflicts with note

## Required outputs
- Scene file completed with mandatory fields.
- Events appended.
- Follow-up tasks generated.

## Exit gate
- Scene task is `DONE` only if scene has at least one event and no unresolved blocker.

## Failure handling
- If scene cannot satisfy chapter purpose, reopen parent chapter outline task and mark current scene task `BLOCKED`.
