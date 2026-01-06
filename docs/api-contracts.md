# API Contracts

## Authentication & Authorization
- Standard: OAuth 2.0 (Authorization Code + Client Credentials for service accounts)
- Tokens: JWT with claims including `tenant_id`, `roles`, `scopes`
- RBAC: `viewer`, `analyst`, `admin` roles

## Ingestion API
### POST `/v1/events`
**Description:** Ingest a batch of events for analytics processing.

**Headers:**
- `Authorization: Bearer <jwt>`
- `Content-Type: application/json`

**Request (example):**
```json
{
  "events": [
    {
      "event_type": "page_view",
      "timestamp": "2026-01-06T15:21:00Z",
      "payload": {"url": "/pricing", "referrer": "/home"}
    },
    {
      "event_type": "purchase",
      "timestamp": "2026-01-06T15:21:02Z",
      "payload": {"order_id": "o-123", "amount": 49.99, "currency": "USD"}
    }
  ]
}
