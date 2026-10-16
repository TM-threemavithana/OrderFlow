# Test Strategy and Quality Gates

## Pyramid / test layers

1. **Domain unit**: pure Java, no Spring context, in-memory collaborations.
2. **Service unit**: business orchestration mocked only at external boundaries.
3. **Web slice**: MVC routing, validation, serialized errors, authorization.
4. **Integration**: PostgreSQL Testcontainers, migrations, JPA, transaction boundaries.
5. **Messaging**: outbox events, consumer duplicate handling, controlled failures.
6. **End-to-end**: minimal payment simulator lifecycle and authorization.
7. **Concurrency / performance**: repeatable simultaneous purchases, baseline profiling.

## Case suite

| ID | Test target | Expected result |
|---|---|---|
| TEST-001 | Empty cart checkout | Rejected, no order |
| TEST-002 | Money `BigDecimal` rounding | Exact expected monetary result |
| TEST-003 | Invalid quantity | Rejected |
| TEST-004 | Last stock two concurrent checkouts | At most one succeeds |
| TEST-005 | Repeat idempotency key same request | One order; previous equivalent result |
| TEST-006 | Repeat key changed request | Conflict |
| TEST-007 | Payment callback duplicate | One effective state change |
| TEST-008 | Payment failure | Reserve released once |
| TEST-009 | Customer A reads B's order | Forbidden or masked 404 as documented |
| TEST-010 | Admin create product unauthorized | Denied |
| TEST-011 | Order tx rollback | No partial persisted state |
| TEST-012 | Outbox same transaction | Both business change and event or neither |
| TEST-013 | Cache invalidation | New admin price reflected after update |
| TEST-014 | Order cannot ship before payment | Invalid transition |
| TEST-015 | App bootstrap clean DB | All migrations pass |

## Definition of done for each task

- Acceptance test(s) authored.
- Successful commands reported with actual exit status; failures recorded and fixed or filed.
- No assertion based solely on test coverage percentage.
- Code review covers correctness, scope, thread safety, security and readability.
- `PROGRESS.md` updated with test evidence and next task.
- Student can explain the feature and 3–5 related interview questions.

## CI gates later

Compile, unit, integration with appropriate services, formatting, dependency audit, container image checks and artifact generation. Avoid unnecessary secret-bearing CI steps.
