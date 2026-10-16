# Architecture Decision Log

## ADR-000 — Learning-first modular monolith (Accepted at planning stage)

**Context:** A beginner-to-advanced portfolio project must prioritize understanding, testing and controlled progression.

**Decision:** Begin with pure Java; transition to a single Spring Boot deployable application organized into business modules; expand only as requirements justify complexity.

**Considered:** Microservices from day one; monolithic feature-layer-only organization.

**Consequences:** Simpler debugging and transactions initially; rich later experiments are still possible. Requires discipline around module boundaries.

## ADR-001 — Payments must be simulated (Accepted)

Avoid real banking/card processing and compliance exposure; use deterministic fake provider scenarios.

## ADR-002 — Database-first consistency before Kafka (Accepted)

Protect core inventory/order invariants with correct SQL/transaction design before introducing asynchronous event delivery.

## ADR-003 — Java 21 LTS as development baseline (Accepted)

**Context:** The starter documentation initially noted a preference for Java 25 LTS. Workstation toolchain discovery confirmed that OpenJDK 21.0.6 LTS (Eclipse Adoptium Temurin) and Oracle JDK 17.0.9 are installed locally. Java 21 is an established Long-Term Support release providing all required language features (records, pattern matching, sealed classes, sequenced collections, and virtual threads).

**Decision:** Standardize on Java 21 LTS as the official language and runtime baseline for OrderFlow. Set Maven compilation target to Java 21 (`<maven.compiler.release>21</maven.compiler.release>`) and align the active shell environment via `$env:JAVA_HOME` pointing to Eclipse Adoptium JDK 21 without modifying machine-wide system configuration.

**Considered:**
1. Requiring Java 25 LTS: Unnecessary installation overhead and potential instability for early phases.
2. Defaulting to Java 17 LTS: While supported, it lacks virtual thread production features and modern collection improvements explored in Phase 1 concurrency labs (OF-011).

**Consequences:** Stable, reproducible local builds without global environment disruption; full support for modern Java idioms and upcoming Spring Boot 4 requirements.

## Future decisions

When changing technology, create a new ADR capturing context, alternatives, decision, consequences, review date and verification evidence. Do not retroactively silently rewrite prior decisions.
