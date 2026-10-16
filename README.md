# OrderFlow — Antigravity IDE Learning-First Starter Pack

**Prepared 2026-10-16.** This is a **documentation-and-prompts starter pack**, not a runnable Java backend. Source code, dependencies, and infrastructure are intentionally deferred until each learning milestone is approved.

## Start here — exact order

1. Extract this ZIP into a new local `OrderFlow` folder. Do not open the ZIP as the project.
2. Open that **folder** in Antigravity IDE (File → Open Folder).
3. In Antigravity settings select **Request Review** for terminal commands and artifact/plan changes; keep external workspace file access off. Confirm exact labels in your installed version.
4. Open `AGENTS.md`, `docs/ORDERFLOW_MASTER_SPEC.md`, and `docs/LEARNING_ROADMAP.md` yourself.
5. Paste `prompts/00_BOOTSTRAP_AND_REVIEW.md` into the Antigravity Agent conversation (the prompt text is in the file). Ask for a plan only.
6. Review the returned implementation plan. Comment or reject incorrect assumptions. Click **Proceed** only after the plan is reasonable.
7. Have Antigravity check the documentation consistency first (`OF-000`). **Do not generate all application features.**
8. Start `OF-001` using `prompts/01_EXECUTE_SINGLE_TASK.md` and complete each backlog task in order.
9. After each task, request a code review (`prompts/02_REVIEW_AND_TEST.md`); update `docs/PROGRESS.md`, then make a reviewed Git commit.
10. Continue later sessions with `prompts/03_RESUME_SESSION.md`. Use the 23 pattern exercises in `docs/DESIGN_PATTERNS_LEARNING_TRACK.md` alongside the relevant milestones.

**If file downloads fail:** the most important files to reconstruct manually are `AGENTS.md`, `docs/ORDERFLOW_MASTER_SPEC.md`, `docs/IMPLEMENTATION_BACKLOG.md`, and `prompts/00_BOOTSTRAP_AND_REVIEW.md`.

## Project route

`Core Java CLI → Spring MVC + PostgreSQL → Security + testing → Concurrency + payment simulation → messaging + cache → delivery + observability`.

Use one **modular monolith**. Microservices are an optional, justified exercise after the baseline operates reliably.

## What is in this archive

- `AGENTS.md`: always-on instruction file for the coding agent.
- `docs/`: requirements, architecture, schema, API, security, testing, milestones, patterns, backlog, tracker, design decisions and trusted learning links.
- `prompts/`: copy/paste prompts for every phase, a reusable per-task prompt, reviews, bug-fixing, learning and session resume.
- `templates/`: acceptance checklist, task card and ADR templates.
- `learning-labs/`: placeholder for Java exercises and design pattern practice; **no source yet**.

## First actions on Windows (PowerShell)

After extraction, open the project folder using Antigravity. Optionally verify tools manually in its terminal:

```powershell
java -version
git --version
mvn -version
```

If Maven is missing, you can later use a generated Maven Wrapper (`mvnw.cmd`) rather than installing Maven globally. Use `Get-Command java,git,mvn -ErrorAction SilentlyContinue` to inspect tool availability without changing your machine.

Do **not** execute destructive cleanup commands or copy secrets into source control.

## Verify actual versions before coding

As of October 2026, Java 21 LTS is the official project baseline (ADR-003) and Spring Boot 4.1.x is planned for Phase 2. The agent must confirm dependencies using official references when generating code. Do not copy Spring Boot 3 dependency coordinates blindly into Boot 4. Spring's `spring-boot-starter-webmvc` supersedes the older `spring-boot-starter-web` starter.

See `docs/RESOURCES.md` for links.
