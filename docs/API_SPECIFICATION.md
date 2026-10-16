# REST API Contract — Planned v1

HTTP interface is introduced during phase 2, not before. Use `/api/v1` namespace. Return typed JSON DTOs; never return JPA entities directly.

| Method | Endpoint | Permission | Meaning |
|---|---|---|---|
| GET | `/api/v1/products` | Guest | Search, page and filter active products |
| GET | `/api/v1/products/{id}` | Guest | Product details |
| POST | `/api/v1/products` | Admin | Create unique SKU |
| PATCH | `/api/v1/products/{id}` | Admin | Partial update |
| POST | `/api/v1/inventory/{productId}/restock` | Staff/admin | Audited restock |
| GET | `/api/v1/cart` | Customer | Own cart |
| POST | `/api/v1/cart/items` | Customer | Add/increment items |
| PATCH | `/api/v1/cart/items/{itemId}` | Customer | Adjust quantity |
| DELETE | `/api/v1/cart/items/{itemId}` | Customer | Remove item |
| POST | `/api/v1/orders` | Customer | Idempotent checkout |
| GET | `/api/v1/orders` | Customer | Own order history |
| GET | `/api/v1/orders/{id}` | Owner/staff as justified | Order details |
| POST | `/api/v1/orders/{id}/cancel` | Owner/staff as justified | Eligible cancellation |
| POST | `/api/v1/orders/{id}/fulfill` | Staff | Begin allowed fulfillment |

## Representative request

```http
POST /api/v1/orders
Authorization: Bearer <test-access-token>
Idempotency-Key: checkout-0001
Content-Type: application/json

{"items":[{"productId":"test-product-id","quantity":2}],"shippingAddressId":"test-address-id"}
```

Client must not supply authoritative prices, customer ID, staff role, or payment success. User comes from verified authentication context.

## Behavior to specify per endpoint before implementation

- Examples for valid body, success response, and error response.
- Status code (201 create, 400 invalid input, 401 unauthenticated, 403 forbidden, 404 missing/hidden resource, 409 conflict, 422 if deliberately chosen and justified).
- Pagination boundaries and stable sorting.
- Field constraints and authorization.
- Idempotency scope + TTL + fingerprint rules.
- HTTP cache semantics when appropriate.
- Error shape: `type`, `title`, `status`, `detail`, `instance`, `traceId` where justified; never expose internal exceptions.

Document contracts with OpenAPI once framework phase begins. Keep API backward-compatible when modifying it.
