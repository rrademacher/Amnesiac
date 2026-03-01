# Process Evaluation — Findings and Adjustments

## What worked
- Linear playbook flow reduced ambiguity and kept task provenance clear.
- Append-only event logging made continuity tracking straightforward.
- Task cascade requirements encouraged downstream planning.

## Friction discovered
1. **Foreshadowing debt lookup was underspecified** in `CO-01` (no explicit source file/format).
2. **"Relevant entities and active plot files" lacked concrete paths**, forcing guesswork.
3. **Missing-entity follow-up was implied but not explicit**, making continuity warnings easy to ignore.

## Remediation applied
Updated `playbooks/playbook_chapter_outline.md` to:
- explicitly reference `canon/story_bible.md`, `canon/entities/`, and `build/projections/plot_status.md`;
- define how to identify foreshadowing debt from `todo/todo_master.md`;
- explicitly require spawning missing-entity tasks when new IDs appear without canonical records.

## Overall assessment
The workflow is viable for a solo author + AI loop. Biggest gains came from making preflight inputs explicit. Without that patch, run quality depends too heavily on operator intuition.
