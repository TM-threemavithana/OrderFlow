# OrderFlow — Ordered Implementation Backlog
Follow numerical order for mandatory tasks. A task is **not approved** merely because listed here. Ask for a scoped plan, review and approve.

| ID | Phase | Task | Prerequisite | Completion proof |
|---|---|---|---|---|
| OF-000 | Preparation | Document and environment review | None | Documentation consistent; conflicts or missing tools reported; user approves next task |
| OF-001 | Core Java | Create Java CLI Maven lab | OF-000 | CLI runs; tests run via Maven wrapper; README includes commands |
| OF-002 | Core Java | Types, Product and Money | OF-001 | Product and Money tests cover invalid price, currency and exact totals |
| OF-003 | Core Java | Encapsulation and inventory invariants | OF-002 | No negative stock; impossible transitions rejected; tests cover boundaries |
| OF-004 | Core Java | Cart composition and collections | OF-003 | Add/update/remove, empty cart and duplicate product tests pass |
| OF-005 | Core Java | Generics, in-memory repositories and Optional | OF-004 | Find/save/remove tests; generic type checks; no global static state |
| OF-006 | Core Java | Polymorphism and Strategy | OF-005 | Two strategies interchangeable; no duplicate business logic; tests |
| OF-007 | Core Java | Exceptions, enums, records and validation | OF-006 | Illegal quantities/state rejected; no catch-and-ignore; tests |
| OF-008 | Core Java | Order domain and state machine | OF-007 | Order totals correct; valid/invalid state transitions tested |
| OF-009 | Core Java | Streams, dates, file IO and reports | OF-008 | Date-aware order summary and sample export with predictable format; tests |
| OF-010 | Core Java | JUnit, mock boundaries and refactoring | OF-009 | Meaningful tests for domain; no unnecessary mocking; review evidence |
| OF-011 | Core Java | Core Java concurrency/JVM lab | OF-010 | Reproducible race demonstration and corrected synchronized test; explain limits |
| OF-012 | Spring & Data | Create Spring Boot 4 REST application | OF-011 | Boot app starts; `/actuator/health` later, first controller smoke test now; BOM/versions checked |
| OF-013 | Spring & Data | IoC, beans and REST controllers | OF-012 | GET product and simple POST behavior tested; controller stays thin |
| OF-014 | Spring & Data | DTO validation and error contracts | OF-013 | 400 for malformed request, 404 for missing resource; no stack trace leak |
| OF-015 | Spring & Data | PostgreSQL + Docker Compose + Flyway | OF-014 | Fresh DB migrates from empty; no hard-coded credentials; indexes justified |
| OF-016 | Spring & Data | SQL and JDBC before ORM | OF-015 | Hand-written queries pass; explain query performance and safe parameter binding |
| OF-017 | Spring & Data | JPA, Hibernate and repositories | OF-016 | Tests against real PostgreSQL; N+1 reproduced and corrected |
| OF-018 | Spring & Data | Transactional order checkout | OF-017 | Order and inventory commit atomically; rollback test; no oversell requirement planned for OF-025 |
| OF-019 | Spring & Data | REST contract and OpenAPI | OF-018 | Endpoints documented with example responses; contract tests |
| OF-020 | Security & Quality | Authentication with OIDC/JWT | OF-019 | 401 invalid/expired token; principal resolved; no custom JWT crypto |
| OF-021 | Security & Quality | Authorization and object ownership | OF-020 | Customer A cannot access B; customer cannot admin mutate; staff rules tested |
| OF-022 | Security & Quality | Testing architecture and Testcontainers | OF-021 | Normal/boundary/failure/security cases pass; repeatable from fresh DB |
| OF-023 | Security & Quality | Architecture boundaries and patterns | OF-022 | No cycles/illegal internal imports; design decisions recorded |
| OF-024 | Security & Quality | Payment adapter and state policies | OF-023 | Approve/decline/timeout and state transitions all tested; no real payments |
| OF-025 | Advanced Systems | Race-safe inventory under load | OF-024 | Two buyers last item: <=1 success; stress tests reliable and repeatable |
| OF-026 | Advanced Systems | Idempotent checkout | OF-025 | Same key+request same logical result; changed payload conflict; parallel duplicate tested |
| OF-027 | Advanced Systems | Payment retries and compensation | OF-026 | Success/failure/timeout/duplicate callbacks cannot double-effect |
| OF-028 | Advanced Systems | Transactional outbox and Kafka | OF-027 | Committed order has event; duplicate events safe; broker outage recoverable |
| OF-029 | Advanced Systems | Redis caching and invalidation | OF-028 | Product updated -> cache consistent within documented rule; Redis outage graceful |
| OF-030 | Advanced Systems | Resilience and external boundaries | OF-029 | Payment simulator outage controlled; retry counts bounded and measured |
| OF-031 | Production | Docker and GitHub Actions CI | OF-030 | Fresh clone one-command local setup; CI passes and reports tests |
| OF-032 | Production | Observability and troubleshooting | OF-031 | Trace one request through logs; readiness distinguishes dependency failure |
| OF-033 | Production | Load tests and JVM profiling | OF-032 | Repeatable benchmark with before/after data; no ungrounded speed claims |
| OF-034 | Production | Deployment, backup and incident runbook | OF-033 | Deployment documented or safely simulated; restore rehearsed; runbook usable |
| OF-035 | Portfolio | Capstone review and interview evidence | OF-034 | Reproducible demo, portfolio case study, 10 technical Q&A with evidence |
| OF-036 | Optional | Microservices/gRPC/WebFlux comparison lab | OF-035 | Documented experiment with latency/operability costs; no forced migration |

## Full task cards

### OF-000 — Document and environment review
- **Phase:** Preparation
- **Prerequisite:** None
- **Concepts/objective:** Inspect ZIP and workspace, reconcile constraints; verify readme/spec/backlog, without writing Java
- **Likely files:** AGENTS.md; docs/*.md (adjust after workspace inspection)
- **Acceptance criteria:** Documentation consistent; conflicts or missing tools reported; user approves next task
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-000.md`

### OF-001 — Create Java CLI Maven lab
- **Phase:** Core Java
- **Prerequisite:** OF-000
- **Concepts/objective:** Verify JDK, Git, Maven/Wrapper; create learning-labs/core-java with Java entry point and first JUnit smoke test
- **Likely files:** learning-labs/core-java/pom.xml; src/main; src/test (adjust after workspace inspection)
- **Acceptance criteria:** CLI runs; tests run via Maven wrapper; README includes commands
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-001.md`

### OF-002 — Types, Product and Money
- **Phase:** Core Java
- **Prerequisite:** OF-001
- **Concepts/objective:** Primitive/reference types, constructors, records, validation, BigDecimal, Currency; immutable product pricing
- **Likely files:** domain/Product.java; domain/Money.java; tests (adjust after workspace inspection)
- **Acceptance criteria:** Product and Money tests cover invalid price, currency and exact totals
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-002.md`

### OF-003 — Encapsulation and inventory invariants
- **Phase:** Core Java
- **Prerequisite:** OF-002
- **Concepts/objective:** Encapsulation, access modifiers, domain methods, exceptions; stock entity with available/reserved
- **Likely files:** domain/Inventory.java; tests (adjust after workspace inspection)
- **Acceptance criteria:** No negative stock; impossible transitions rejected; tests cover boundaries
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-003.md`

### OF-004 — Cart composition and collections
- **Phase:** Core Java
- **Prerequisite:** OF-003
- **Concepts/objective:** Composition, List vs Map, equals/hashCode; Cart/CartItem and quantity validation
- **Likely files:** domain/Cart.java; CartItem.java; tests (adjust after workspace inspection)
- **Acceptance criteria:** Add/update/remove, empty cart and duplicate product tests pass
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-004.md`

### OF-005 — Generics, in-memory repositories and Optional
- **Phase:** Core Java
- **Prerequisite:** OF-004
- **Concepts/objective:** Interfaces, generics, Map storage, Optional/null semantics; repository port
- **Likely files:** repository interfaces; in-memory adapters; tests (adjust after workspace inspection)
- **Acceptance criteria:** Find/save/remove tests; generic type checks; no global static state
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-005.md`

### OF-006 — Polymorphism and Strategy
- **Phase:** Core Java
- **Prerequisite:** OF-005
- **Concepts/objective:** Abstraction, overriding/overloading, interfaces, SOLID, strategy for shipping/discount
- **Likely files:** domain/DiscountPolicy; strategies; tests (adjust after workspace inspection)
- **Acceptance criteria:** Two strategies interchangeable; no duplicate business logic; tests
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-006.md`

### OF-007 — Exceptions, enums, records and validation
- **Phase:** Core Java
- **Prerequisite:** OF-006
- **Concepts/objective:** Custom domain exceptions, enum status, error boundaries and immutable DTO records
- **Likely files:** domain exceptions; status; DTO records (adjust after workspace inspection)
- **Acceptance criteria:** Illegal quantities/state rejected; no catch-and-ignore; tests
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-007.md`

### OF-008 — Order domain and state machine
- **Phase:** Core Java
- **Prerequisite:** OF-007
- **Concepts/objective:** Order aggregate, order items, price snapshot, factory vs constructors, invariants
- **Likely files:** domain/Order; OrderItem; tests (adjust after workspace inspection)
- **Acceptance criteria:** Order totals correct; valid/invalid state transitions tested
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-008.md`

### OF-009 — Streams, dates, file IO and reports
- **Phase:** Core Java
- **Prerequisite:** OF-008
- **Concepts/objective:** Streams, collectors, java.time, NIO, serialization pitfalls and logging basics
- **Likely files:** CLI reports; utilities; tests (adjust after workspace inspection)
- **Acceptance criteria:** Date-aware order summary and sample export with predictable format; tests
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-009.md`

### OF-010 — JUnit, mock boundaries and refactoring
- **Phase:** Core Java
- **Prerequisite:** OF-009
- **Concepts/objective:** Unit test design, parameterized tests, AssertJ, safe Mockito use, debugger, SOLID refactor
- **Likely files:** refactor + test suite (adjust after workspace inspection)
- **Acceptance criteria:** Meaningful tests for domain; no unnecessary mocking; review evidence
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-010.md`

### OF-011 — Core Java concurrency/JVM lab
- **Phase:** Core Java
- **Prerequisite:** OF-010
- **Concepts/objective:** Thread basics, ExecutorService, locks, futures, memory visibility, virtual threads overview, JFR basics
- **Likely files:** learning-labs/core-java concurrency tests (adjust after workspace inspection)
- **Acceptance criteria:** Reproducible race demonstration and corrected synchronized test; explain limits
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-011.md`

### OF-012 — Create Spring Boot 4 REST application
- **Phase:** Spring & Data
- **Prerequisite:** OF-011
- **Concepts/objective:** Verify current Spring Boot 4.x and Java support, Maven starters; create backend module without duplicating domain logic
- **Likely files:** backend/pom.xml; backend/src (adjust after workspace inspection)
- **Acceptance criteria:** Boot app starts; `/actuator/health` later, first controller smoke test now; BOM/versions checked
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-012.md`

### OF-013 — IoC, beans and REST controllers
- **Phase:** Spring & Data
- **Prerequisite:** OF-012
- **Concepts/objective:** DI vs manual wiring, bean scopes, MVC request lifecycle, HTTP methods, DTO boundaries
- **Likely files:** backend controllers and services; MVC tests (adjust after workspace inspection)
- **Acceptance criteria:** GET product and simple POST behavior tested; controller stays thin
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-013.md`

### OF-014 — DTO validation and error contracts
- **Phase:** Spring & Data
- **Prerequisite:** OF-013
- **Concepts/objective:** Bean Validation, @RestControllerAdvice, standardized errors, pagination basics
- **Likely files:** DTOs; validators; exception advice; tests (adjust after workspace inspection)
- **Acceptance criteria:** 400 for malformed request, 404 for missing resource; no stack trace leak
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-014.md`

### OF-015 — PostgreSQL + Docker Compose + Flyway
- **Phase:** Spring & Data
- **Prerequisite:** OF-014
- **Concepts/objective:** Schema, constraints, migration workflow, environment variables, connection pools
- **Likely files:** compose.yml; Flyway SQL migrations (adjust after workspace inspection)
- **Acceptance criteria:** Fresh DB migrates from empty; no hard-coded credentials; indexes justified
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-015.md`

### OF-016 — SQL and JDBC before ORM
- **Phase:** Spring & Data
- **Prerequisite:** OF-015
- **Concepts/objective:** Joins, grouping, transactions, PreparedStatement, indexes, explain analyze
- **Likely files:** SQL exercise/DAO; integration tests (adjust after workspace inspection)
- **Acceptance criteria:** Hand-written queries pass; explain query performance and safe parameter binding
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-016.md`

### OF-017 — JPA, Hibernate and repositories
- **Phase:** Spring & Data
- **Prerequisite:** OF-016
- **Concepts/objective:** Entity lifecycle, mappings, lazy/eager, N+1, repository queries, projections
- **Likely files:** entities; repos; Testcontainers tests (adjust after workspace inspection)
- **Acceptance criteria:** Tests against real PostgreSQL; N+1 reproduced and corrected
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-017.md`

### OF-018 — Transactional order checkout
- **Phase:** Spring & Data
- **Prerequisite:** OF-017
- **Concepts/objective:** Service boundaries, rollback, atomic inventory reservation, price snapshots
- **Likely files:** ordering service; integration tests (adjust after workspace inspection)
- **Acceptance criteria:** Order and inventory commit atomically; rollback test; no oversell requirement planned for OF-025
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-018.md`

### OF-019 — REST contract and OpenAPI
- **Phase:** Spring & Data
- **Prerequisite:** OF-018
- **Concepts/objective:** HTTP semantic consistency, versioned API, pagination, safe data mapping
- **Likely files:** OpenAPI setup; API docs; tests (adjust after workspace inspection)
- **Acceptance criteria:** Endpoints documented with example responses; contract tests
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-019.md`

### OF-020 — Authentication with OIDC/JWT
- **Phase:** Security & Quality
- **Prerequisite:** OF-019
- **Concepts/objective:** Spring Security filters, OAuth2/OIDC, signed JWT resource-server checks; fake/test identity provider
- **Likely files:** security configuration; integration tests (adjust after workspace inspection)
- **Acceptance criteria:** 401 invalid/expired token; principal resolved; no custom JWT crypto
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-020.md`

### OF-021 — Authorization and object ownership
- **Phase:** Security & Quality
- **Prerequisite:** OF-020
- **Concepts/objective:** RBAC, object-level rules, admin restrictions, auditing, OWASP API risks
- **Likely files:** access policy; security tests (adjust after workspace inspection)
- **Acceptance criteria:** Customer A cannot access B; customer cannot admin mutate; staff rules tested
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-021.md`

### OF-022 — Testing architecture and Testcontainers
- **Phase:** Security & Quality
- **Prerequisite:** OF-021
- **Concepts/objective:** Slice vs service vs integration vs E2E testing, real PG, deterministic fixtures, CI-friendly tests
- **Likely files:** test support and integration suite (adjust after workspace inspection)
- **Acceptance criteria:** Normal/boundary/failure/security cases pass; repeatable from fresh DB
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-022.md`

### OF-023 — Architecture boundaries and patterns
- **Phase:** Security & Quality
- **Prerequisite:** OF-022
- **Concepts/objective:** Module ownership, dependency inversion, repository/adapter/facade, Spring Modulith optional
- **Likely files:** module verification tests; ADR (adjust after workspace inspection)
- **Acceptance criteria:** No cycles/illegal internal imports; design decisions recorded
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-023.md`

### OF-024 — Payment adapter and state policies
- **Phase:** Security & Quality
- **Prerequisite:** OF-023
- **Concepts/objective:** Adapter and State patterns when justified, test doubles, fake payment provider behavior
- **Likely files:** payment simulator; tests (adjust after workspace inspection)
- **Acceptance criteria:** Approve/decline/timeout and state transitions all tested; no real payments
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-024.md`

### OF-025 — Race-safe inventory under load
- **Phase:** Advanced Systems
- **Prerequisite:** OF-024
- **Concepts/objective:** Transactions, isolation, optimistic vs pessimistic locking, atomic conditional UPDATE
- **Likely files:** inventory concurrency tests (adjust after workspace inspection)
- **Acceptance criteria:** Two buyers last item: <=1 success; stress tests reliable and repeatable
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-025.md`

### OF-026 — Idempotent checkout
- **Phase:** Advanced Systems
- **Prerequisite:** OF-025
- **Concepts/objective:** Idempotency-Key scope, persisted request fingerprints/results, collision and retry policy
- **Likely files:** idempotency storage and tests (adjust after workspace inspection)
- **Acceptance criteria:** Same key+request same logical result; changed payload conflict; parallel duplicate tested
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-026.md`

### OF-027 — Payment retries and compensation
- **Phase:** Advanced Systems
- **Prerequisite:** OF-026
- **Concepts/objective:** Backoff, bounded retries, duplicate callbacks, reservation expiry, compensation
- **Likely files:** payment async workflow; tests (adjust after workspace inspection)
- **Acceptance criteria:** Success/failure/timeout/duplicate callbacks cannot double-effect
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-027.md`

### OF-028 — Transactional outbox and Kafka
- **Phase:** Advanced Systems
- **Prerequisite:** OF-027
- **Concepts/objective:** Outbox pattern, event publishing, at-least-once, idempotent consumer
- **Likely files:** outbox migration; Kafka publisher/consumer (adjust after workspace inspection)
- **Acceptance criteria:** Committed order has event; duplicate events safe; broker outage recoverable
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-028.md`

### OF-029 — Redis caching and invalidation
- **Phase:** Advanced Systems
- **Prerequisite:** OF-028
- **Concepts/objective:** Cache-aside, TTL, invalidation, stale reads, cache safety
- **Likely files:** catalog caching; tests (adjust after workspace inspection)
- **Acceptance criteria:** Product updated -> cache consistent within documented rule; Redis outage graceful
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-029.md`

### OF-030 — Resilience and external boundaries
- **Phase:** Advanced Systems
- **Prerequisite:** OF-029
- **Concepts/objective:** Timeouts, bounded retry, circuit breaker, backpressure and failure budgets
- **Likely files:** adapter resilience tests (adjust after workspace inspection)
- **Acceptance criteria:** Payment simulator outage controlled; retry counts bounded and measured
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-030.md`

### OF-031 — Docker and GitHub Actions CI
- **Phase:** Production
- **Prerequisite:** OF-030
- **Concepts/objective:** Layered builds, Compose, env configuration, Maven cache, tests and dependency scanning
- **Likely files:** Dockerfile; compose; workflows (adjust after workspace inspection)
- **Acceptance criteria:** Fresh clone one-command local setup; CI passes and reports tests
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-031.md`

### OF-032 — Observability and troubleshooting
- **Phase:** Production
- **Prerequisite:** OF-031
- **Concepts/objective:** Actuator health, structured logging, correlation IDs, Micrometer, OpenTelemetry
- **Likely files:** metrics logs traces configuration (adjust after workspace inspection)
- **Acceptance criteria:** Trace one request through logs; readiness distinguishes dependency failure
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-032.md`

### OF-033 — Load tests and JVM profiling
- **Phase:** Production
- **Prerequisite:** OF-032
- **Concepts/objective:** JFR, memory analysis, GC, p50/p95, index optimization, connection pool tuning
- **Likely files:** scripts/benchmarks; benchmark reports (adjust after workspace inspection)
- **Acceptance criteria:** Repeatable benchmark with before/after data; no ungrounded speed claims
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-033.md`

### OF-034 — Deployment, backup and incident runbook
- **Phase:** Production
- **Prerequisite:** OF-033
- **Concepts/objective:** Secure nonpaid deployment, config/secrets, backup/restore, rollback, release discipline
- **Likely files:** docs/runbook; deployment configuration (adjust after workspace inspection)
- **Acceptance criteria:** Deployment documented or safely simulated; restore rehearsed; runbook usable
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-034.md`

### OF-035 — Capstone review and interview evidence
- **Phase:** Portfolio
- **Prerequisite:** OF-034
- **Concepts/objective:** Architecture walkthrough, ADR review, tradeoffs, README, demo, mock interviews
- **Likely files:** README; docs/portfolio-case-study.md (adjust after workspace inspection)
- **Acceptance criteria:** Reproducible demo, portfolio case study, 10 technical Q&A with evidence
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-035.md`

### OF-036 — Microservices/gRPC/WebFlux comparison lab
- **Phase:** Optional
- **Prerequisite:** OF-035
- **Concepts/objective:** Compare modular monolith to extraction; learn tradeoffs; microservice only if justified
- **Likely files:** optional lab (adjust after workspace inspection)
- **Acceptance criteria:** Documented experiment with latency/operability costs; no forced migration
- **Review:** Student explanation; normal, boundary and failure tests; actual command results; update `PROGRESS.md` before advancing.
- **Prompt:** `prompts/tasks/OF-036.md`
