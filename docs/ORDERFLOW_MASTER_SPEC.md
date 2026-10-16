# OrderFlow — Master Project Specification

Status: **Planned**. No implementation is implied by these documents.

## Purpose

Build and understand a realistic, secure, testable Java backend, growing one domain capability at a time. The learning objective takes priority over feature velocity. Deliver an interview-ready portfolio proving engineering judgment rather than an AI-generated demonstration.

## Product description

A single-store simulated commerce/order-management backend with customers, catalog, carts, stock reservation, order checkout, fake payments, shipping states, notifications, staff actions and audit trail. At first it is a terminal program, then an HTTP backend, then a production-style modular monolith.

## Actors

Guest (browse only); Customer (cart, checkout, own orders); Staff (fulfillment and stock management); Admin (catalog and roles); External payment simulator (fake callbacks); Scheduled jobs (expiry/retry); System operator (metrics/diagnostics).

## Functional scope

- Customer identity and profiles; distinguish identity provider user subject from local customer record.
- Catalog: SKU uniqueness, name, price+currency, active flag, category, pagination/filtering.
- Cart: add/update/remove; validate quantity and product availability; totals recalculated server-side.
- Inventory: on-hand, reserved, available; atomic reservation and release; stock changes with audit.
- Orders: create, read, cancel, history; immutable item-price snapshots; explicit state machine.
- Payment: fake provider supports approved, rejected, timed out, callback duplicate, delayed and refund; no real processor and no real cards.
- Fulfillment: pack, ship and deliver; prevent transitions that violate payment/order state.
- Notifications: order created/paid/shipped simulation; event delivery with idempotent consumers later.
- Admin: role-specific inventory and product management.
- Audit: who/what/when for sensitive changes, with privacy limits.

## High-priority invariants

1. Never oversell: each successful reservation conserves stock.
2. No lost or duplicate effects from repeated order requests and payment events.
3. Prices and user ownership are determined by trusted server-side state.
4. Every state transition is authorized and valid.
5. Persistent domain changes remain transactionally consistent.
6. No secrets in Git/logs; no real card information.
7. New tasks do not break verified earlier behavior.

## Phases

0. Documentation and workstation checks.
1. Core Java CLI with in-memory repositories, OOP and unit tests.
2. Spring MVC REST, SQL, Flyway, JPA and transactional workflows.
3. OIDC/JWT authorization, testing, modular boundaries, clean refactoring.
4. Concurrency, idempotency, simulated payments, outbox/Kafka, Redis, resilience.
5. Containers, continuous integration, observability, profiling, secure deployment and runbooks.
Optional: Batch, WebFlux, gRPC, CQRS or microservice extraction only with a documented justification.

## Nonfunctional requirements (progressively measured)

- Correctness: invariants held under unit/integration/concurrency tests.
- Security: object-level authorization and request validation tested.
- Maintainability: domain-focused packages, clear boundaries, readable ADRs.
- Reliability: retry and failure-recovery experiments documented.
- Performance: record reproducible baseline workload and measurements; do not invent SLOs.
- Operability: health and diagnostic signals, safe configuration, tested backup/restore.

## Avoid in initial implementation

Real payments, front-end scope creep, premature microservices, unnecessary abstraction, paid cloud dependencies, bespoke authentication or cryptography, and cosmetic adoption of every design pattern.

## Working principle

For every task: theory → small self-attempt → feedback → tests → debugging → explanation → documentation → approved next task.

See: `SOFTWARE_REQUIREMENTS.md`, `ARCHITECTURE.md`, `LEARNING_ROADMAP.md`, `IMPLEMENTATION_BACKLOG.md`.
