# Software Requirements Specification (SRS)

All requirements are **planned**. Acceptance tests are progressively implemented.

| ID | Requirement | Acceptance evidence |
|---|---|---|
| FR-001 | Admin maintains uniquely keyed products | Duplicate SKU rejected; authorized create/update tests |
| FR-002 | Guests browse active products | Pagination and inactive-product visibility tested |
| FR-003 | Customer manages a cart | Add/change/remove/empty-cart tests |
| FR-004 | Checkout validates all inputs | Invalid quantity, removed product and price tampering rejected |
| FR-005 | Order total is server calculated | Tested `BigDecimal` arithmetic and currency consistency |
| FR-006 | Inventory reserve/release atomic | Parallel checkout cannot oversell; cancellation returns reserves |
| FR-007 | Orders have explicit valid state transitions | Invalid transition produces meaningful domain error |
| FR-008 | Idempotent checkout | Duplicate key + same request gives previous result; different request conflicts |
| FR-009 | Fake payment states and callbacks | Success/failure/timeout/duplicate/retry scenarios tested |
| FR-010 | Authorized users view their own orders | Unauthenticated, forbidden and cross-account tests |
| FR-011 | Staff fulfills paid orders | Cannot ship unpaid or cancelled order |
| FR-012 | Significant changes have audit events | Actor, action, resource, time captured safely |
| FR-013 | Notifications follow order changes | Event delivery and duplicate tolerance tested |
| FR-014 | Admin can manage inventory | Authorized restock and concurrency tests |
| FR-015 | Customers list order history | Pagination, sorting, security and status filtering |

## Nonfunctional criteria

| ID | Requirement | Verification |
|---|---|---|
| NFR-001 | Reproducible local build | Fresh machine instructions + successful build |
| NFR-002 | No secrets committed | `.gitignore`, scanning and review |
| NFR-003 | Correct transaction boundaries | Real PostgreSQL integration tests |
| NFR-004 | Observability | Correlated request logs, health, metrics; eventually traces |
| NFR-005 | Maintainability | Module boundary tests and reviewable ADRs |
| NFR-006 | Resilience | Injection tests for timeouts, retry duplicates, queue outage |
| NFR-007 | Measured performance | Store test method, dataset, p50/p95 latency and resources, not invented targets |
| NFR-008 | Backups | Successful restore rehearsal |

## Assumptions requiring confirmation during implementation

- One store/tenant; single currency per order; taxes/shipping simulated and stated explicitly.
- Small finite product catalog for early versions.
- Local development uses test user identities and sample data.
- Payment simulator is a bounded external-adapter exercise, not a real merchant integration.
- Scope changes must update SRS, backlog, tests and architecture decisions.
