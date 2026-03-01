# Playbook: Editor Feedback Intake

## Purpose
Convert raw editor notes into trackable, dependency-aware tasks and canonical decisions.

## Entry conditions
- New notes exist in `editor/notes_inbox.md`.

## Steps

### EI-01 — Normalize notes
1. Assign each note an ID (`ednote_####`).
2. Label type: continuity, pacing, characterization, clarity, or line-level.
3. Link impacted chapter/scene/entity IDs.

### EI-02 — Decide processing path
1. If note requires canon change, create a decision task and record in `decisions/`.
2. If note is local-only, create direct implementation task.

### EI-03 — Task generation
For each note, create tasks with:
- parent task reference
- depends_on references
- origin_playbook: `playbook_editor_intake.md`
- origin_step: `EI-03`

### EI-04 — Move processed notes
1. Copy processed notes to `editor/notes_resolved.md` with resolution links.
2. Mark inbox entries as processed.

## Required outputs
- Every note has a corresponding task or explicit defer record.
- No unclassified notes remain in inbox.

## Exit gate
- You can trace each editor note to a task ID and final resolution state.
