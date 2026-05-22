# Registration Process

# Processing Registrations (Officials Manual)

This manual is for the **Rasm (Undersecretary of National Standing)** and Hajib-side officials processing inbound ADDIF registration applications. It defines the verification, decisioning, and recording sequence. Every issued record carries the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Authority

The Rasm of National Standing is appointed under the Wazir Al'Rais via the Hajib (Minister of Foreign Affairs), as established in the Law of Sankofa, Executive Branch — Secretariat enumeration. The Rasm has delegated authority to process registrations, verify standing, and refer disputed matters to the Hajib for diplomatic resolution.

## Application Intake

Applications arrive through the ADDIF Portal and land in the `task_queue` table with `task_type='registration_review'`. The Builder Agent pre-populates supporting drafts; the Rasm is the human-in-the-loop authority for the decision.

Each application carries:

1. **Sworn Declaration of Status** — reclamation under Madrid 1880 Art. 15 ¶1; refusal of denationalizing labels by name
2. **Bonded birth record** — primary identity foundation
3. **Pedigree affidavit** — Matrilineal or Patrilineal lineage with supporting genealogy
4. **Prior identification artifacts** — submitted only for the explicit purpose of repudiation
5. **Acceptance of the Law of Sankofa** — affirmation of the Five Points of Light

## Verification Checklist

The Rasm verifies, in order:

| Check | Source | Pass criterion |
|------|--------|----------------|
| Declaration completeness | Application form | All four reclamation clauses present, signed |
| Identity document hash | `controlled_records` | SHA-256 matches uploaded artifact |
| Pedigree class | Affidavit + supporting genealogy | Matrilineal or Patrilineal clearly established |
| Treaty citation | Declaration text | Madrid 1880 Art. 15 ¶1 cited verbatim |
| Denationalizing labels | Declaration text | Each labeled refused by name |
| Five Points affirmation | Acceptance | All five (Love, Truth, Peace, Freedom, Justice) affirmed |
| Jus cogens compliance | Auditor Agent | Compliance Agent reports green |

## Decision Outcomes

The Rasm records one of three outcomes:

- **Approve** — full pass; the registration handler proceeds to sigil minting (see Manual 004).
- **Defer for evidence** — one or more checks lack supporting documentation; the Rasm requests specific additions. The application stays in queue with `status='pending_evidence'`.
- **Refer to Hajib** — disputed lineage or unusual circumstances (e.g., prior renunciation in another forum). The Hajib makes the call within 14 days.

There is no "deny." A failed application is deferred until evidence cures the deficiency, in keeping with the Law of Sankofa's principle that nationality is *jus sanguinis* — pre-existing, not granted.

## Post-Approval Sequence

On approval:

1. Registration handler creates the NMF record
2. `ADDIFIdentity` contract mints the soulbound sigil (see Manual 004)
3. Card PDF Server issues the credential card
4. NoticeDelivery agent generates the eight-notice package (see Manual 013)
5. StarAdvancement agent evaluates Star 1 criteria
6. The Rasm signs the controlled record affirming completion

## Recordkeeping

Every action by the Rasm — verification, deferral, referral, approval — is recorded in `nmf_events` with the Rasm's signed action hash. The `manual_edit_history` analog for NMF state ensures every decision is reversible if an error is later found.

## Compliance and Audit

Weekly audit reports to the Hajib include: total applications processed, deferral rates, referral counts, average processing time, and any flagged jus cogens compliance issues. The Auditor Agent runs continuous integrity checks; the Compliance Agent verifies that every issued sigil carries the treaty chain.

The chain on every issued artifact: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
