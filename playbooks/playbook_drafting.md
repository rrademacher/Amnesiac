# Playbook: Drafting Handoff and Draft Validation

## Purpose
Prepare an outline-complete chapter package so a human author can draft prose without continuity hunting, then validate and reconcile the first prose draft before publication.

## Entry conditions
- All required scene outlines for the chapter are marked done.
- No blocking continuity conflicts remain.

## Steps

### DR-01 — Build draft packet
1. Compile chapter purpose, beats, and ordered scenes into `chapters/ch##/draft_packet.md`.
2. Include character/location quick-reference tables.

### DR-02 — Include constraints and open questions
1. Add non-negotiable canon constraints.
2. Add unresolved but non-blocking questions in a separate section.

### DR-03 — Author instructions
1. Write explicit drafting targets (tone, pacing, stakes progression).
2. List scene-by-scene minimum outcomes.

### DR-04 — Mark handoff status
1. Update task graph: set chapter drafting handoff task to `DONE`.
2. Create follow-up task for post-draft event reconciliation.

### DR-05 — Generate chapter prose draft file
1. Create initial prose draft in `chapters/ch##/drafts/ch##_v01.md` (or next available version if re-running after a rejected draft).
2. Ensure the draft contains all scenes represented in `ch##_outline.md` and associated scene files.

### DR-06 — Run outline conformance check
1. Compare `chapters/ch##/drafts/ch##_v##.md` against `ch##_outline.md` and chapter scene files.
2. Verify every outlined beat has textual evidence in the draft.
3. Verify each scene's mandatory outcomes are explicitly satisfied.
4. Run canon consistency pass against entities and timeline references.

### DR-07 — Classify deviations
1. Record any outline-vs-draft deviations in a review log.
2. Tag each deviation as one of:
   - `intentional` (improves draft without violating constraints),
   - `fix-required` (quality/coverage issue),
   - `canon-breaking` (contradiction with entities, timeline, or non-negotiable constraints).

### DR-08 — Revise and re-check loop
1. If any deviation is tagged `fix-required` or `canon-breaking`, revise the draft and increment version (`ch##_v02.md`, etc.).
2. Re-run DR-06 and DR-07 after each revision.
3. Continue until acceptance criteria are met or `max_revision_passes` is reached.
4. If `max_revision_passes` is reached without acceptance, escalate to planning/continuity review before publication.

### DR-09 — Publish accepted draft and reconcile
1. Mark latest accepted version as publish candidate (e.g., copy/link as `chapters/ch##/drafts/ch##_accepted.md`).
2. Create reconciliation tasks for:
   - canon updates implied by intentional deviations,
   - timeline/entity register updates,
   - downstream chapter dependency checks.
3. Update task graph with acceptance status and reconciliation task IDs.

## Required outputs
- `chapters/ch##/draft_packet.md` exists.
- Handoff checklist is complete.
- At least one draft file exists in `chapters/ch##/drafts/`.
- Conformance/deviation review log exists for the accepted draft.
- Reconciliation tasks are created if intentional deviations altered canon-adjacent details.

## Acceptance criteria (measurable)
- **Beat evidence coverage:** 100% of beats in `ch##_outline.md` map to at least one explicit text span in the accepted draft.
- **Scene outcome satisfaction:** 100% of mandatory outcomes in chapter scene files are satisfied in the accepted draft.
- **Canon consistency:** 0 unresolved contradictions with canon entities or timeline in the accepted draft.
- **Revision governance:** Total revision passes does not exceed `max_revision_passes` without documented escalation.

## Exit gate
- A new author can open only the draft packet + canon links and start drafting immediately.
- Editorial review can trace every beat and mandatory scene outcome to concrete prose evidence.
- Accepted draft is either canon-consistent or explicitly escalated with blocking issues documented.
