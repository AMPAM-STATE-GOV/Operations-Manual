# Schema

# Database Schema (Developer Manual)

The AMPAM platform's system of record is **Supabase Postgres** (port 8000), accessed primarily via `docker exec supabase-db psql -U postgres`. This manual maps the schema by domain. Every row carries — implicitly or explicitly via `jurisdictional_basis` — the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Knowledge and Documentation

| Table | Purpose |
|-------|---------|
| `knowledge_base` | Paragraph-chunked source documents (Constitution, Treaties, Decrees, READMEs) for agent grounding |
| `manual_sections` | The Nationals / Officials / Developers manuals, with version history in `manual_edit_history` |
| `manual_edit_history` | Append-only history of section edits (previous + new content, editor, reason, version) |

## National Master File (NMF)

The pivot tables for per-National state:

| Table | Purpose |
|-------|---------|
| `national_master_file` | The National's core record — identity, pedigree, Star tier, status |
| `nmf_documents` | Every document filed under or for the National; `jurisdictional_basis` column carries the chain at row level |
| `nmf_document_storage` | Encrypted blob storage referenced by `nmf_documents` |
| `nmf_events` | Lifecycle and audit events bound to the National |
| `nmf_transactions` | Financial actions involving the National |
| `nmf_correspondence` | Inbound and outbound correspondence |
| `national_profiles` | Display/profile data |
| `foundational_documents` | Originating evidence (bonded birth record, pedigree affidavit, etc.) |
| `controlled_records` | Every controlled record carrying the chain |

## Governance

| Table | Purpose |
|-------|---------|
| `governance_documents` | Constitutions, treaties, charters, decrees, proclamations |
| `governance_articles` | Articles of a `governance_documents` row (parent-child structure) |
| `treaty_obligations` | Obligations a party owes under a specific treaty |
| `treaty_participants` | Signatories and protégé states |
| `governance_rules` | Operational governance rules referenced by agents |
| `governance_requests` | Requests for governance action |
| `governance_approvals` | Approvals/denials of governance requests |
| `governance_enforcement_log` | Enforcement actions taken |
| `policies` | Policy text under governance |
| `policy_decisions` | Decisions recorded against policies |

## ADDIF Registry

Issued credentials (`addif_credentials`, `addif_credential_cards`), estates (`addif_estates`), per-National roles in an estate (`addif_person_estate_roles`), claims (`addif_claims`), generated notices (`addif_auto_notices`), recovery state (`addif_recovery`), verification scans (`addif_scan_events`), and the sovereign domain namespace (`addif_domains`, `domain_registry`, `registry_anchors`).

## On-Chain Bridge

ALDC token state (`aldc_balances`, `aldc_transactions`) and `bridge_events` between Postgres and chain.

## Agents and Automation

`agent_definitions` (the seven workers), `agent_runs` (per-invocation log), `agent_governance_authority` (agent-to-authority mapping), `notification_queue` (outbound), `notice_delivery_log` (delivery state), `audit_events` (cross-cutting audit log).

## Identity, Control, and Custody

`controllers` (controlling identities), `entities` (legal entities — AMPAM, institutions, sub-entities), the control plane (`control_ledger`, `control_events`, `control_transfers`, `control_locks`, `control_disputes`, `control_revocations`), claim handling (`claims`, `claim_evidence`, `claim_events`, `claim_control_link`), asset positions (`interest_holdings`, `assets`).

## Operational

`api_keys` (Bridge API keys), `app_analytics`/`app_deployments` (observability), `instrument_templates`/`instruments` (templates and issued instruments), `federation_nodes` (federated AMPAM nodes — see Developer Manual 003).

For exact column-level schema, run `\d <table>` in `psql`.

The chain on every row: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
