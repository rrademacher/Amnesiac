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
