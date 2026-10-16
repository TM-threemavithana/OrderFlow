# OrderFlow — Learning Roadmap (Strict Implementation Order)
The dates and durations are adjustable. **No task is complete because an AI agent says so: record actual tests and student explanations.**

**Time planning:** around 26–32 weeks at 10–12 focused study hours/week, but use skill gates rather than deadlines. Apply for work throughout; this is a learning plan, not a job guarantee.

| Phase | Suggested focus | Exit gate |
|---|---|---|
| Preparation (`OF-000`–`OF-000`) | Document and environment review | Spec validated, tool availability known, review approved |
| Core Java (`OF-001`–`OF-011`) | Create Java CLI Maven lab, Types, Product and Money, Encapsulation and inventory invariants … | CLI business flow and unit tests pass without Spring; explain OOP |
| Spring & Data (`OF-012`–`OF-019`) | Create Spring Boot 4 REST application, IoC, beans and REST controllers, DTO validation and error contracts … | REST API persists complete orders with PostgreSQL migration and rollback tests |
| Security & Quality (`OF-020`–`OF-024`) | Authentication with OIDC/JWT, Authorization and object ownership, Testing architecture and Testcontainers … | OAuth2/JWT, object authorization, real-DB integration tests pass |
| Advanced Systems (`OF-025`–`OF-030`) | Race-safe inventory under load, Idempotent checkout, Payment retries and compensation … | Race and retry tests prove no oversell or double effect; failure experiments recorded |
| Production (`OF-031`–`OF-034`) | Docker and GitHub Actions CI, Observability and troubleshooting, Load tests and JVM profiling … | Container, CI, observable logs, benchmarks and recovery docs verified |
| Portfolio (`OF-035`–`OF-035`) | Capstone review and interview evidence | Public-safe explanatory case study and demo reproducible |
| Optional (`OF-036`–`OF-036`) | Microservices/gRPC/WebFlux comparison lab | Chosen only after graduation from core roadmap |

## Detailed step order

### Preparation
- [ ] **OF-000 — Document and environment review**: Inspect ZIP and workspace, reconcile constraints; verify readme/spec/backlog, without writing Java. *Gate:* Documentation consistent; conflicts or missing tools reported; user approves next task.
### Core Java
- [ ] **OF-001 — Create Java CLI Maven lab**: Verify JDK, Git, Maven/Wrapper; create learning-labs/core-java with Java entry point and first JUnit smoke test. *Gate:* CLI runs; tests run via Maven wrapper; README includes commands.
- [ ] **OF-002 — Types, Product and Money**: Primitive/reference types, constructors, records, validation, BigDecimal, Currency; immutable product pricing. *Gate:* Product and Money tests cover invalid price, currency and exact totals.
- [ ] **OF-003 — Encapsulation and inventory invariants**: Encapsulation, access modifiers, domain methods, exceptions; stock entity with available/reserved. *Gate:* No negative stock; impossible transitions rejected; tests cover boundaries.
- [ ] **OF-004 — Cart composition and collections**: Composition, List vs Map, equals/hashCode; Cart/CartItem and quantity validation. *Gate:* Add/update/remove, empty cart and duplicate product tests pass.
- [ ] **OF-005 — Generics, in-memory repositories and Optional**: Interfaces, generics, Map storage, Optional/null semantics; repository port. *Gate:* Find/save/remove tests; generic type checks; no global static state.
- [ ] **OF-006 — Polymorphism and Strategy**: Abstraction, overriding/overloading, interfaces, SOLID, strategy for shipping/discount. *Gate:* Two strategies interchangeable; no duplicate business logic; tests.
- [ ] **OF-007 — Exceptions, enums, records and validation**: Custom domain exceptions, enum status, error boundaries and immutable DTO records. *Gate:* Illegal quantities/state rejected; no catch-and-ignore; tests.
- [ ] **OF-008 — Order domain and state machine**: Order aggregate, order items, price snapshot, factory vs constructors, invariants. *Gate:* Order totals correct; valid/invalid state transitions tested.
- [ ] **OF-009 — Streams, dates, file IO and reports**: Streams, collectors, java.time, NIO, serialization pitfalls and logging basics. *Gate:* Date-aware order summary and sample export with predictable format; tests.
- [ ] **OF-010 — JUnit, mock boundaries and refactoring**: Unit test design, parameterized tests, AssertJ, safe Mockito use, debugger, SOLID refactor. *Gate:* Meaningful tests for domain; no unnecessary mocking; review evidence.
- [ ] **OF-011 — Core Java concurrency/JVM lab**: Thread basics, ExecutorService, locks, futures, memory visibility, virtual threads overview, JFR basics. *Gate:* Reproducible race demonstration and corrected synchronized test; explain limits.
### Spring & Data
- [ ] **OF-012 — Create Spring Boot 4 REST application**: Verify current Spring Boot 4.x and Java support, Maven starters; create backend module without duplicating domain logic. *Gate:* Boot app starts; `/actuator/health` later, first controller smoke test now; BOM/versions checked.
- [ ] **OF-013 — IoC, beans and REST controllers**: DI vs manual wiring, bean scopes, MVC request lifecycle, HTTP methods, DTO boundaries. *Gate:* GET product and simple POST behavior tested; controller stays thin.
- [ ] **OF-014 — DTO validation and error contracts**: Bean Validation, @RestControllerAdvice, standardized errors, pagination basics. *Gate:* 400 for malformed request, 404 for missing resource; no stack trace leak.
- [ ] **OF-015 — PostgreSQL + Docker Compose + Flyway**: Schema, constraints, migration workflow, environment variables, connection pools. *Gate:* Fresh DB migrates from empty; no hard-coded credentials; indexes justified.
- [ ] **OF-016 — SQL and JDBC before ORM**: Joins, grouping, transactions, PreparedStatement, indexes, explain analyze. *Gate:* Hand-written queries pass; explain query performance and safe parameter binding.
- [ ] **OF-017 — JPA, Hibernate and repositories**: Entity lifecycle, mappings, lazy/eager, N+1, repository queries, projections. *Gate:* Tests against real PostgreSQL; N+1 reproduced and corrected.
- [ ] **OF-018 — Transactional order checkout**: Service boundaries, rollback, atomic inventory reservation, price snapshots. *Gate:* Order and inventory commit atomically; rollback test; no oversell requirement planned for OF-025.
- [ ] **OF-019 — REST contract and OpenAPI**: HTTP semantic consistency, versioned API, pagination, safe data mapping. *Gate:* Endpoints documented with example responses; contract tests.
### Security & Quality
- [ ] **OF-020 — Authentication with OIDC/JWT**: Spring Security filters, OAuth2/OIDC, signed JWT resource-server checks; fake/test identity provider. *Gate:* 401 invalid/expired token; principal resolved; no custom JWT crypto.
- [ ] **OF-021 — Authorization and object ownership**: RBAC, object-level rules, admin restrictions, auditing, OWASP API risks. *Gate:* Customer A cannot access B; customer cannot admin mutate; staff rules tested.
- [ ] **OF-022 — Testing architecture and Testcontainers**: Slice vs service vs integration vs E2E testing, real PG, deterministic fixtures, CI-friendly tests. *Gate:* Normal/boundary/failure/security cases pass; repeatable from fresh DB.
- [ ] **OF-023 — Architecture boundaries and patterns**: Module ownership, dependency inversion, repository/adapter/facade, Spring Modulith optional. *Gate:* No cycles/illegal internal imports; design decisions recorded.
- [ ] **OF-024 — Payment adapter and state policies**: Adapter and State patterns when justified, test doubles, fake payment provider behavior. *Gate:* Approve/decline/timeout and state transitions all tested; no real payments.
### Advanced Systems
- [ ] **OF-025 — Race-safe inventory under load**: Transactions, isolation, optimistic vs pessimistic locking, atomic conditional UPDATE. *Gate:* Two buyers last item: <=1 success; stress tests reliable and repeatable.
- [ ] **OF-026 — Idempotent checkout**: Idempotency-Key scope, persisted request fingerprints/results, collision and retry policy. *Gate:* Same key+request same logical result; changed payload conflict; parallel duplicate tested.
- [ ] **OF-027 — Payment retries and compensation**: Backoff, bounded retries, duplicate callbacks, reservation expiry, compensation. *Gate:* Success/failure/timeout/duplicate callbacks cannot double-effect.
- [ ] **OF-028 — Transactional outbox and Kafka**: Outbox pattern, event publishing, at-least-once, idempotent consumer. *Gate:* Committed order has event; duplicate events safe; broker outage recoverable.
- [ ] **OF-029 — Redis caching and invalidation**: Cache-aside, TTL, invalidation, stale reads, cache safety. *Gate:* Product updated -> cache consistent within documented rule; Redis outage graceful.
- [ ] **OF-030 — Resilience and external boundaries**: Timeouts, bounded retry, circuit breaker, backpressure and failure budgets. *Gate:* Payment simulator outage controlled; retry counts bounded and measured.
### Production
- [ ] **OF-031 — Docker and GitHub Actions CI**: Layered builds, Compose, env configuration, Maven cache, tests and dependency scanning. *Gate:* Fresh clone one-command local setup; CI passes and reports tests.
- [ ] **OF-032 — Observability and troubleshooting**: Actuator health, structured logging, correlation IDs, Micrometer, OpenTelemetry. *Gate:* Trace one request through logs; readiness distinguishes dependency failure.
- [ ] **OF-033 — Load tests and JVM profiling**: JFR, memory analysis, GC, p50/p95, index optimization, connection pool tuning. *Gate:* Repeatable benchmark with before/after data; no ungrounded speed claims.
- [ ] **OF-034 — Deployment, backup and incident runbook**: Secure nonpaid deployment, config/secrets, backup/restore, rollback, release discipline. *Gate:* Deployment documented or safely simulated; restore rehearsed; runbook usable.
### Portfolio
- [ ] **OF-035 — Capstone review and interview evidence**: Architecture walkthrough, ADR review, tradeoffs, README, demo, mock interviews. *Gate:* Reproducible demo, portfolio case study, 10 technical Q&A with evidence.
### Optional
- [ ] **OF-036 — Microservices/gRPC/WebFlux comparison lab**: Compare modular monolith to extraction; learn tradeoffs; microservice only if justified. *Gate:* Documented experiment with latency/operability costs; no forced migration.

## Pattern-learning overlay
Complete the applicable real-use patterns in production when needed; study remaining GoF patterns as separate labs after OF-010, using `DESIGN_PATTERNS_LEARNING_TRACK.md`. Each pattern lab requires one minimal example, a failure/problem story and at least two tests.

## Stage transition checklist
Before introducing Spring, student can independently design and test Product/Cart/Order. Before Kafka, order consistency must work in PostgreSQL. Before cloud, the app must run locally reproducibly and safely.
