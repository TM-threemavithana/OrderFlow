# Windows + Antigravity Setup (no destructive commands)

1. Create `C:\Projects\OrderFlow` in Explorer; extract ZIP **contents** into it, so `AGENTS.md` sits directly in project root.
2. In Antigravity IDE choose File → Open Folder → `C:\Projects\OrderFlow`.
3. Confirm you can see `AGENTS.md`, `README.md`, `docs/`, `prompts/`.
4. In Agent settings select **Terminal auto execution: Request Review** and **Artifact review: Request Review**. Keep access outside workspace disabled unless explicitly required.
5. In Agent pane use `prompts/00_BOOTSTRAP_AND_REVIEW.md`; its `/plan` command creates a plan for review.
6. Inspect plan for Java-first sequence, exact task scope and tests; comment if necessary; click Proceed only when acceptable.
7. In terminal (only after approval), diagnose tool availability:

```powershell
Get-Command java,git,mvn -ErrorAction SilentlyContinue
java -version
git --version
mvn -version
```

8. Missing tool? Use maintained official download sources and ask for instructions first. Do not blindly modify PATH or reinstall Java. Maven Wrapper generated at first task can avoid machine-global Maven.
9. Git repository initialization only after inspecting the current directory and getting permission (do not initialize inside another unrelated repo).
10. After OF-001 add a README run command and a green JUnit smoke test.

## Common problems

- **Antigravity ignores instructions:** verify `AGENTS.md` in actual workspace root; reload the correct folder; explicitly ask the agent to read the file.
- **Download appears empty:** extract ZIP before opening folder; Windows may block some downloaded archives—verify publisher/context before unblocking.
- **`java` not found:** JDK install/PATH issue; inspect `Get-Command` and `JAVA_HOME`; do not edit globally until you understand current settings.
- **Maven not found:** use Maven Wrapper once approved; `mvnw.cmd` is Windows wrapper command, `./mvnw` on Unix-like shells.
- **Wrong Spring tutorial:** align starter names and dependencies with current Spring Boot 4.x docs; do not mix major-version examples.
- **Agent implements too much:** stop run, ask to revert only unapproved diffs after inspection; point to backlog scope and AGENTS.md.
