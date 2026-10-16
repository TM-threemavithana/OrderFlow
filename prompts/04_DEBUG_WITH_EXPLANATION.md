# Use if a task fails

Help me debug OrderFlow task [TASK-ID]. Read relevant files and the failing test/stack trace first. Give a short hypothesis list ordered by likelihood, what evidence would confirm each, and small safe experiments. Do not replace broad sections of working code or suppress exceptions to make tests green. Explain the root cause and ask me to try the smallest fix before generating a complete patch. After a fix, run the failing test and the related regression suite, report actual results, and record the cause in `docs/PROGRESS.md`.
