# Playbook: Integrity Check (Lightweight)

## Entry conditions
1. You have updated or generated any canon, chapter, scene, entity, or event file.
2. `STYLEGUIDE.md` is available and includes current ID prefix rules.

## Actions
1. Compile referenced IDs from changed files (event `entities`, `plots`, launch cast references, and inline canonical mentions).
2. Verify canonical record coverage for each referenced ID:
   - `char_####`, `loc_####`, `org_####`, `plot_####`, `theme_####` appear in canonical sources (for current repo state, validate against `canon/story_bible.md` and any entity files present under `canon/entities/`).
3. Verify prefixes match `STYLEGUIDE.md` conventions:
   - Reject `fac_####`; normalize to `org_####`.
   - Ensure chapter IDs use `ch##` and scene IDs use `ch##_sc##`.
4. For each event record, verify `chapter_id` and `scene_id` exist:
   - Chapter exists under `chapters/<chapter_id>/`.
   - Scene file exists under `chapters/<chapter_id>/scenes/<scene_id>.md`.
5. Record any mismatch as a blocking issue before merge.

## Outputs
1. A short checklist result with pass/fail for:
   - Referenced ID has canonical record.
   - Prefixes conform to style guide.
   - Event chapter/scene IDs resolve to existing files.
2. A remediation list for each failure (exact ID, file path, and expected replacement).

## Exit gate
1. All three checklist categories pass, OR
2. Failures are documented with explicit remediation tasks created before handoff.

## Failure handling
1. If canonical records are missing, add placeholder canonical entries or open a tracked task before proceeding.
2. If prefix mismatch is found, update IDs to canonical form and re-run the checklist.
3. If chapter/scene path is missing, either create the missing file stub or correct the event reference to an existing ID.
