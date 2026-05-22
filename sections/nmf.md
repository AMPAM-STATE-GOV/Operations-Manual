# Nmf

# National Master File

The **National Master File (NMF)** is the single source of truth for each AMPAM National. Every act touching a National's record — registration, sigil mint, document upload, encounter, advancement, consular notification — passes through the NMF and is preserved with the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## What the NMF Contains

The NMF is a structured aggregate of related tables, all keyed to the National's NMF identifier:

| Table | Holds |
|-------|-------|
| `national_master_file` | The National's core record — identity, pedigree class, Star tier, status |
| `nmf_documents` | Every document filed under or for the National (with jurisdictional_basis defaulted to *"Madrid Protocol 1880 → AMPAM → ADDIF Registry"*) |
| `nmf_document_storage` | Encrypted storage of document content |
| `nmf_events` | Every event — verifications, advancements, encounters, consular notifications, audits |
| `nmf_transactions` | Financial actions tied to the National (Treasury distributions, fees) |
| `nmf_correspondence` | All correspondence sent and received on the National's behalf |
| `foundational_documents` | The originating evidence (see Manual 016) |
| `controlled_records` | Every controlled record carrying the chain |

The `nmf_documents` table is the central pivot — each row carries the jurisdictional basis on its own column, which means the treaty chain is preserved at the row level, not only at the artifact level.

## NMF Counters

Every insert/delete into `nmf_documents` fires `trg_nmf_doc_counter` to update aggregate counts. The Auditor Agent reads these daily to confirm record integrity.

## Provenance Chain

Every NMF row carries provenance that points back through the chain:

1. **Artifact-level** — SHA-256 hash on every document and instrument
2. **Treaty-level** — the `jurisdictional_basis` column carries the chain
3. **Governance-level** — `governance_provenance` (JSONB) references the AMPAM article or decree under which the act was taken
4. **Treaty-references** — `treaty_references` (JSONB) lists the specific treaties cited by the artifact

## Access and Read Patterns

The NMF is accessed through three pathways:

- **National Portal** — the National's own view; sees their NMF record in full
- **Dashboard API** (port 9500) — officials' read/write access; scoped by role (Rasm, Hajib, Mufti, Qazi)
- **Agents** — the seven autonomous workers read and write via the `task_queue` table with `FOR UPDATE SKIP LOCKED` concurrency

Direct SQL access is restricted to Hajib-level officials and audit-mode actions, with every query logged.

## Lifecycle Events

Major NMF lifecycle events:

| Event | Trigger | Records to |
|-------|---------|------------|
| `created` | First foundational document verified | `nmf_events`, NMF row created |
| `sigil_minted` | ADDIFIdentity contract mint | `nmf_events`, on-chain record |
| `star_advanced` | StarAdvancement Agent passes criteria | `nmf_events`, NMF row updated |
| `encounter_filed` | National files an encounter record | `nmf_events`, `nmf_documents` |
| `consular_notification` | Detention notice received/sent | `nmf_events`, `nmf_correspondence` |
| `terminated` | National's death | `nmf_events`, NMF row status set to terminated |

## Compliance

The **Compliance Agent** audits the NMF continuously:

- Each `nmf_documents` row must carry a non-null `jurisdictional_basis`
- Each artifact's SHA-256 must verify against its stored content
- Each expired instrument must be flagged within 24 hours of expiration
- Each Star advancement must be supported by the prerequisite controlled records

## Backup and Recovery

The NMF is included in the nightly backup. Backups are encrypted at rest. Recovery procedures require Hajib authorization, and any recovery action is itself logged as an `nmf_event` of type `recovery`.

The chain anchoring every NMF row: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
