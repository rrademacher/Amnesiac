# Playbook: Retcon and Canon Change Control

## Purpose
Handle canon-affecting changes safely with explicit decisions, task cascades, and reversible history.

## Entry conditions
- A conflict or desired change affects existing canon/events.

## Steps

### RC-01 — Open decision record
1. Create `decisions/dec_YYYYMMDD_##.md` from template.
2. Document:
   - current canon
   - proposed canon
   - reason
   - impact radius (chapters/scenes/entities)

### RC-02 — Branch recommendation
1. If using Git, create retcon branch (`retcon/<scope>-<desc>`).
2. Keep unrelated changes out of this branch.

### RC-03 — Apply minimal canonical updates
1. Update canonical entity/story bible files.
2. Append compensating events where needed; do not silently rewrite history.

### RC-04 — Cascade tasks
Create tasks for:
- affected chapter/scene outline updates
- foreshadowing backfill in earlier chapters
- projection regeneration and continuity verification

### RC-05 — Verification gate
1. Regenerate projections.
2. Resolve or acknowledge every new contradiction.

## Required outputs
- Decision record completed.
- Canon changes linked to decision ID.
- Cascaded tasks created.

## Exit gate
- Retcon is traceable, reversible, and all blockers are represented in task graph.
