# Database & Transactions — Planned Schema

Implement PostgreSQL only in phase 2. **Schema below is a proposal** and must be reviewed before committing Flyway migrations.

| Table | Key columns | Important rules |
|---|---|---|
| customers | id, subject, email, created_at | subject unique; email normalization policy |
| addresses | id, customer_id, fields | ownership FK; data privacy |
| categories | id, name | unique category name as appropriate |
| products | id, sku, name, price_amount, price_currency, active | SKU unique, price >= 0 |
| inventory | product_id, on_hand, reserved, version | reserved>=0, on_hand>=reserved, optimistic version |
| carts | id, customer_id | customer ownership |
| cart_items | cart_id, product_id, quantity | positive quantity; unique cart+product |
| orders | id, customer_id, status, total_amount, currency, created_at | valid state enum/check |
| order_items | id, order_id, product_id, quantity, unit_price_amount, currency | price snapshot; positive qty |
| payments | id, order_id, provider_reference, status, amount, currency | idempotency/uniqueness |
| shipments | id, order_id, status, tracking_ref | no shipment before valid payment state |
| idempotency_keys | customer_id, operation, key, request_hash, result, status | unique scope+key; conflict on changed payload |
| outbox_events | id, aggregate_type, aggregate_id, type, payload, published_at | written transactionally; retries possible |
| audit_events | id, actor_subject, action, resource, timestamp | no passwords/token payloads |

## Required experiments

1. Explain primary vs foreign vs unique/check constraints.
2. Build schema using Flyway, inspect migration history.
3. Measure normal `SELECT` with and without index (`EXPLAIN ANALYZE`).
4. Reproduce N+1 and fix with deliberate fetch planning or DTO projection.
5. Test transaction rollback in real PostgreSQL.
6. Concurrently purchase one remaining item; no overselling.
7. Demonstrate DB isolation differences and the consequences.
8. Demonstrate idempotent retry stored results and conflict detection.
9. Prove database write and outbox append commit atomically.

Never use floating point for money. Prefer NUMERIC/DECIMAL and `BigDecimal`; document rounding/tax choices. Database constraints supplement application validation; they do not replace it.
