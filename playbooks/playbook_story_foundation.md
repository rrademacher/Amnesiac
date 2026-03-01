# Playbook: Story Foundation Bootstrap

## Purpose
Establish prerequisite story foundations before chapter-level outlining begins: core purpose/theme, an initial story bible scaffold, and a minimal launch cast.

## Entry conditions
- Repository is available locally.
- `todo/active_task.md` points to a foundation/bootstrap task or startup triage indicates missing foundations.
- You can edit `canon/`, `todo/`, and `build/projections/` files.

## Steps

### SF-01 — Confirm startup prerequisites
1. Read `canon/story_bible.md`.
2. Confirm the following foundation fields exist and are specific (not placeholders):
   - story premise
   - story purpose statement
   - thematic spine
   - initial plotline seed
3. Read `canon/entities/README.md` and confirm minimal cast requirements are documented.

### SF-02 — Define story intent
1. In `canon/story_bible.md`, write:
   - one-paragraph premise
   - one-paragraph purpose statement (what the story is trying to say)
   - 3 to 5 themes with IDs (`theme_####`)
2. Add at least one active plotline with explicit stakes.

### SF-03 — Establish minimal cast and world anchors
1. Create canonical entity records for a minimum viable launch set:
   - at least 1 protagonist (`char_####`)
   - at least 1 opposing force character or faction (`char_####` or `fac_####`)
   - at least 2 launch locations (`loc_####`)
2. For each entity record, include canonical facts, motivations/function, and initial unknowns.

### SF-04 — Create kickoff tasks
1. Add or update `todo/todo_master.md` tasks for:
   - chapter 1 outline initialization
   - scene placeholder creation
   - any unresolved canon/entity gaps found during bootstrap
2. Ensure each task includes `origin_playbook: playbook_story_foundation.md` and relevant `origin_step`.

### SF-05 — Mark readiness
1. Update `build/projections/continuity_report.md` with a startup readiness section:
   - foundation complete / incomplete
   - known gaps that are non-blocking
2. Mark foundation task `DONE` only if prerequisites and kickoff tasks are present.

## Required outputs
- `canon/story_bible.md` contains premise, purpose, themes, and initial plot stakes.
- Minimal cast/location records exist in `canon/entities/`.
- Startup tasks exist in `todo/todo_master.md`.

## Exit gate
- A new operator can begin chapter outlining without inventing global story intent from scratch.

## Failure handling
- If you cannot establish canon-safe foundations due to conflicting constraints, open `playbook_retcon.md` and create a decision record before proceeding.
