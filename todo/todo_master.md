# Master Task Graph

Use this file as canonical task queue.

## Status legend
- `NEXT`: ready to execute now
- `WAITING`: blocked by dependencies
- `DONE`: completed
- `BLOCKED`: cannot progress due to unresolved issue
- `DEFERRED`: intentionally postponed with rationale

## Tasks

- id: task_000001
  title: Initialize chapter 1 outline
  status: DONE
  priority: 1
  parent: null
  depends_on: []
  origin_playbook: playbook_start_here.md
  origin_step: SH-03
  context_files:
    - canon/story_bible.md
    - chapters/ch01/ch01_outline.md

- id: task_000002
  title: Create chapter 1 scene placeholders
  status: DONE
  priority: 2
  parent: task_000001
  depends_on: [task_000001]
  origin_playbook: playbook_chapter_outline.md
  origin_step: CO-03
  context_files:
    - chapters/ch01/ch01_outline.md

- id: task_000003
  title: Build chapter 1 drafting packet
  status: DONE
  priority: 3
  parent: task_000001
  depends_on: [task_000002]
  origin_playbook: playbook_drafting.md
  origin_step: DR-01
  context_files:
    - chapters/ch01/
    - build/projections/

- id: task_000004
  title: Create canonical entity records for new IDs introduced in ch01 events
  status: NEXT
  priority: 1
  parent: task_000001
  depends_on: [task_000001]
  origin_playbook: playbook_chapter_outline.md
  origin_step: CO-05
  context_files:
    - chapters/ch01/events/ch01_events.ndjson
    - canon/entities/README.md
    - build/projections/continuity_report.md

- id: task_000005
  title: Post-draft event reconciliation for chapter 1 prose draft
  status: WAITING
  priority: 2
  parent: task_000003
  depends_on: [task_000003]
  origin_playbook: playbook_drafting.md
  origin_step: DR-04
  context_files:
    - chapters/ch01/draft_packet.md
    - chapters/ch01/events/ch01_events.ndjson
