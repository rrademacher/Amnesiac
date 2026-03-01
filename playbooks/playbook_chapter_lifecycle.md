# Playbook: Chapter Lifecycle State Machine

## Purpose
Define the required chapter states, artifacts, and transition gates from outline readiness through lock, including controlled opening of the next chapter.

## States
1. `outline_ready`
2. `scenes_ready`
3. `draft_ready`
4. `draft_complete`
5. `reviewed`
6. `locked`

## Required artifacts per state

### `outline_ready`
- Required:
  - `chapters/chNN/chNN_outline.md` (outline)
  - `chapters/chNN/events/chNN_events.ndjson` (event log initialized)

### `scenes_ready`
- Required:
  - `chapters/chNN/chNN_outline.md` (outline)
  - `chapters/chNN/scenes/chNN_sc*.md` (scene files covering planned sequence)
  - `chapters/chNN/events/chNN_events.ndjson` (event log)

### `draft_ready`
- Required:
  - `chapters/chNN/chNN_outline.md` (outline)
  - `chapters/chNN/scenes/chNN_sc*.md` (scene files)
  - `chapters/chNN/draft_packet.md` (draft packet)
  - `chapters/chNN/events/chNN_events.ndjson` (event log)

### `draft_complete`
- Required:
  - `chapters/chNN/chNN_outline.md` (outline)
  - `chapters/chNN/scenes/chNN_sc*.md` (scene files)
  - `chapters/chNN/draft_packet.md` (draft packet)
  - `chapters/chNN/chNN_draft.md` (draft text)
  - `chapters/chNN/events/chNN_events.ndjson` (event log, reconciled for draft deltas)

### `reviewed`
- Required:
  - All `draft_complete` artifacts
  - `editor/notes_inbox.md` entries linked to `chNN`
  - `chapters/chNN/chNN_review_notes.md` (review notes and disposition summary)

### `locked`
- Required:
  - All `reviewed` artifacts
  - `editor/notes_resolved.md` entries for resolved/accepted chapter notes
  - Lock marker in chapter task chain (chapter lifecycle task status `DONE`)

## Transition gates and failure handling

### Gate: `outline_ready` → `scenes_ready`
- Pass when each required scene file exists and maps to outline beats.
- Failure handling:
  - Mark lifecycle task `BLOCKED`.
  - Create remediation task(s) for missing/misaligned scenes.
  - Do not advance state until resolved.

### Gate: `scenes_ready` → `draft_ready`
- Pass when `draft_packet.md` is complete and references canon constraints.
- Failure handling:
  - Mark drafting-prep task `BLOCKED`.
  - Add task for packet completion or continuity cleanup.

### Gate: `draft_ready` → `draft_complete`
- Pass when `chNN_draft.md` exists and events are reconciled in `chNN_events.ndjson`.
- Failure handling:
  - Mark draft completion task `WAITING` if prose incomplete, `BLOCKED` if continuity conflict found.
  - Add explicit fix task for each blocking issue.

### Gate: `draft_complete` → `reviewed`
- Pass when review notes are captured and each note has a disposition (accept, defer, reject with reason).
- Failure handling:
  - Keep chapter in `draft_complete`.
  - Create note-resolution child tasks with dependencies.

### Gate: `reviewed` → `locked`
- Pass when accepted edits are applied, resolved notes are logged, and no blocking TODOs remain for `chNN`.
- Failure handling:
  - Reopen chapter to `draft_complete` (if prose changes needed) or remain `reviewed` (if documentation only).
  - Record rationale in notes and task comments.

## Step: Open next chapter

### LC-OPEN-NEXT — Initialize `chNN+1`
1. Confirm `chNN` is either:
   - state `locked`, or
   - intentionally parallelized (explicit task note: reason, risk, and owner).
2. Create `chapters/chNN+1/` with standard subfolders as needed (`scenes/`, `events/`).
3. Seed `chapters/chNN+1/chNN+1_outline.md` from the current chapter handoff context.
4. Create/queue tasks for chapter `NN+1` outline and scene planning.

## Exit criteria
- Current chapter has an explicitly recorded lifecycle state.
- No state transition is performed without required artifacts and gate checks.
- Next chapter initialization occurs only through `LC-OPEN-NEXT`.
