# Security Threat Model & Controls

Security is mandatory but phased. Use only synthetic identities and simulated payments.

## Assets and boundaries

- Access tokens and identity provider verification.
- Customer records, addresses, order history, role assignment.
- Server-side prices, inventory and payment outcomes.
- Admin mutations and internal event payloads.
- Secrets, DB and event broker credentials.

## Threats → tests

| Threat | Control | Required evidence |
|---|---|---|
| Cross-customer order access (BOLA) | Resource ownership checks | Customer A cannot read B's order |
| Privilege escalation | Role/permission checks server-side | Customer cannot create products or fulfill orders |
| JWT misuse | OIDC/JWT resource-server validation | Invalid signature, issuer, audience or expiry rejected |
| Price tampering | Server-side catalog lookup | Client-submitted price ignored/rejected |
| Injection | Parameterized SQL/JPA and validated inputs | Malformed filters cannot alter SQL |
| Duplicate checkout/payment | Idempotency key and state machine | Duplicate effect prevented |
| Secrets leaks | Env-based secrets, no sensitive logs | Git review/scanning |
| Excessive use | Request limits and backpressure where appropriate | Load/abuse tests |
| Missing audit | Staff changes logged without tokens | Audit record assertions |
| Dependency compromise | Vulnerability scanning, reviewed updates | CI evidence |

## Implementation notes

- Learn authentication vs authorization separately.
- Prefer a maintained OAuth2/OIDC provider. Let Spring Security verify tokens; never implement custom JWT signing/cryptography for login.
- Configure least privilege; default deny. Consider object-scoped access before responding.
- Treat CORS as a browser policy, not an access-control mechanism. CSRF requirements depend on authentication mechanism; analyze rather than blindly disable.
- Avoid real payment details, card data, confidential personal information.
- Map errors without disclosing SQL, stack traces or credentials.

## Reference baseline

OWASP API Security Top 10 (2023), OWASP ASVS (5.0), Spring Security reference, and current NIST SSDF guidelines. Links in `RESOURCES.md`.
