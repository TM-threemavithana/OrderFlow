# Generic task execution prompt (replace [TASK-ID])

Read `AGENTS.md`, `docs/PROGRESS.md`, and `docs/IMPLEMENTATION_BACKLOG.md`, plus the documents relevant to [TASK-ID]. Inspect the repository.

Please plan **[TASK-ID] only**. Before editing, explain the concepts and give me a small first exercise. Present a reviewable plan with changed files, tests, risks, acceptance criteria and how this task connects to OrderFlow. STOP before coding until I approve or show my attempt.

After approval, implement only this task, verify with real commands and show outputs, do a code review and teach me the key lessons. Update `docs/PROGRESS.md` and relevant ADRs; do not advance to the next task automatically.

For prefilled task-specific prompts see `prompts/tasks/OF-XXX.md`.
