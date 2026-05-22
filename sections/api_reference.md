# Api Reference

# Bridge API Reference (Developer Manual)

The **Bridge API** is the HTTP surface that connects external clients — the Portal, the Dashboard, and accredited integrations — to AMPAM's data plane. It is implemented by `/opt/pdh/scripts/dashboard_api.py` and listens on port **9500**. All authoritative operations sit under this surface, with the chain affirmed in every response envelope: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Architecture Position

The Bridge sits between front-end (Portal `/var/www/pdh/portal.html`, Dashboard `/var/www/pdh/index.html`) and back-end (Supabase Postgres). It routes to Cert Server (`:9100`), AI Proxy (`:9200`), Upload Server (`:9300`), Registry Handler (`:9400`), ALD Gateway (`:9600`), Card PDF Server (`:9700`), and n8n (`:5678`) — without duplicating their functions.

## Authentication

Three authentication levels:

| Level | Caller | Mechanism |
|-------|--------|-----------|
| **Public** | Unauthenticated verification queries | None — read-only access to public records |
| **National** | A Registered National accessing their NMF record | National's controlling key signature |
| **Official** | Rasm, Hajib, Mufti, Qazi acting in office | Role-scoped API key (`api_keys` table) |

Every authenticated call is recorded in `audit_events` with caller identity, timestamp, endpoint, and outcome.

## Endpoint Categories

The endpoints group into seven categories:

| Category | Purpose | Underlying tables |
|----------|---------|-------------------|
| **National** | NMF read/write for the National's own record | `national_master_file`, `nmf_documents`, `nmf_events` |
| **Registration** | Application intake and decisioning | `registration_applications`, `foundational_documents` |
| **Sigil** | On-chain identity status; mint orchestration | `controlled_records`, on-chain `ADDIFIdentity` |
| **Credential** | Card issuance, status, verification | `addif_credential_cards`, `addif_credentials` |
| **Notice** | Notice generation, tracking, escalation | `auto_notices`, `notice_delivery_log` |
| **Domain** | ALD namespace lookups and registrations | `addif_domains`, `domain_registry`, `registry_anchors` |
| **Governance** | Bills, decrees, orders | `governance_documents`, `governance_articles`, `governance_rules` |

For exact route paths, request bodies, and response shapes, the canonical source is `/opt/pdh/scripts/dashboard_api.py`.

## Response Envelope

Every Bridge response wraps payload in a standard envelope:

```json
{
  "ok": true,
  "data": { ... },
  "chain": "Madrid Protocol 1880 → AMPAM → ADDIF Registry",
  "request_id": "<uuid>",
  "ts": "<RFC 3339 timestamp>"
}
```

Error responses set `ok: false` and include `error` and `error_code` fields. The chain is present on every response.

## Idempotency

State-mutating endpoints accept an `Idempotency-Key` header. Duplicate requests within 24 hours return the same response without re-executing. This is required for any endpoint that mints a sigil, generates a notice, or files a controlled record.

## Rate Limits

| Caller class | Default limit |
|--------------|---------------|
| Public | 60 requests / minute |
| National | 300 requests / minute |
| Official | 1200 requests / minute |

Limits are enforced at the reverse-proxy layer (Nginx). Adjustments require Hajib authorization.

## Versioning

The Bridge follows additive-versioning: new fields may be added without a version bump; breaking changes ship under `/v2/`. The currently shipping version is `v1`. Clients should send `Accept: application/vnd.ampam.v1+json`; absent that header, `v1` is the default.

## Recordkeeping

Every Bridge call generates an `audit_events` row. Records of state mutation also generate corresponding rows in the relevant `nmf_events` and `controlled_records` tables.

The chain in every Bridge response: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
