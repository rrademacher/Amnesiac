# Playbook: Story Completion

## Purpose
Close the project with explicit validation that required story, task, and continuity conditions are satisfied before declaring completion.

## Entry conditions
- Repository is available locally.
- Chapter-level tasks are complete or no additional chapter tasks remain executable.
- You can edit `build/projections/` and `todo/` files.

## Steps

### SC-01 — Verify required plotline closure
1. Read `build/projections/plot_status.md`.
2. Verify all required plotlines are either closed or intentionally open with rationale.
3. If any required plotline is unresolved without explicit intent, create blocking remediation tasks before proceeding.

### SC-02 — Verify unresolved tasks are non-blocking
1. Read `todo/todo_master.md`.
2. Confirm any remaining unresolved tasks are explicitly non-blocking for story completion.
3. Reclassify or add dependency notes if a task is still blocking completion.

### SC-03 — Run final continuity reconciliation
1. Perform a final continuity pass against canon constraints, plotline outcomes, and chapter state records.
2. Record any residual continuity risks as non-blocking notes or create blockers if critical.

### SC-04 — Record completion status
1. Update `build/projections/continuity_report.md` with a timestamped completion record.
2. Mark project status complete only after SC-01 through SC-03 pass.

## Required outputs
- Completion validation recorded across plot, task, and continuity checks.
- Timestamped completion entry in `build/projections/continuity_report.md`.

## Exit gate
- Required plotlines are closed or intentionally open.
- Remaining unresolved tasks are non-blocking.
- Continuity reconciliation is complete and documented.
