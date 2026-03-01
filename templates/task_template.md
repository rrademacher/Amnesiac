- id: task_######
  title: <imperative action>
  status: NEXT|WAITING|DONE|BLOCKED|DEFERRED
  priority: <integer>
  parent: <task_id|null>
  depends_on: [<task_id>, ...]
  origin_playbook: <playbook file>
  origin_step: <step id>
  context_files:
    - <relative path>

## Lifecycle transition examples

### Example: `lock_chapter`
- id: task_210100
  title: lock_chapter_ch07
  status: NEXT
  priority: 1
  parent: task_210000
  depends_on: [task_210090]
  origin_playbook: playbooks/playbook_chapter_lifecycle.md
  origin_step: reviewed_to_locked
  context_files:
    - chapters/ch07/ch07_draft.md
    - chapters/ch07/ch07_review_notes.md
    - editor/notes_resolved.md

### Example: `open_next_chapter`
- id: task_210110
  title: open_next_chapter_ch08
  status: NEXT
  priority: 2
  parent: task_210000
  depends_on: [task_210100]
  origin_playbook: playbooks/playbook_chapter_lifecycle.md
  origin_step: LC-OPEN-NEXT
  context_files:
    - chapters/ch07/ch07_outline.md
    - chapters/ch08/ch08_outline.md
    - todo/todo_master.md
