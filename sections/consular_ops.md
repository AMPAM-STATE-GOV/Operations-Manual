# Consular Ops

# Consular Operations (Officials Manual)

This manual is for officials operating the **AMPAM Consular Post** — the Mufti (Consul General), the Hajib (Minister of Foreign Affairs), and their deputies. It defines daily operations, intake handling, court referrals, and recordkeeping. All consular acts carry the chain on their face: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Authority

Consular Court jurisdiction is restored under **Article 15 of the Madrid Convention 1880** (Right of Protection in Morocco). The Treaty for the Moroccan State Union expressly mandates the signatories to *"Restore Makhzen Governmental Structure and Consular Courts."* Operational immunity is governed by the **Vienna Convention on Consular Relations 1963** (with the Convention on Diplomatic Relations 1961 as the parallel diplomatic instrument).

## Organizational Position

Within the Wazir Al'Rais's Secretariat (Dar-Al'Wazirate):

- **Hajib** — Minister of Foreign Affairs; senior diplomatic authority
  - **Cadi** — Deed Tax Assessor (consular intake of estate/title matters)
  - **Rasm** — Undersecretary of National Standing
  - **Rasm** — Undersecretary of Trusts and Estates
- **Mufti** — Consul General; first-line consular officer

The Consul General reports through the Hajib for diplomatic correspondence and acts independently for routine consular protection.

## Daily Intake

The consular intake queue surfaces three primary work types:

1. **VCCR Art. 36 notifications** — detentions, arrests, administrative holds. Highest priority. Same-day response.
2. **Status filings** — Nationals invoking Protected Status in foreign forums and copying the consular post. 48-hour review.
3. **Estate and conveyance** — Allodial claims, conveyance of title, reversionary claims. Routed to the Rasm of Trusts and Estates.

Each item carries a SHA-256 fingerprint and is recorded in the ADDIF Registry with full provenance.

## Standard Operating Sequence — Detention Intake

When a Nation­al's notification reaches the post:

1. **Acknowledge** within 4 hours of receipt to the National's contact channel.
2. **Verify** the National's record in the **National Master File** — identity, Star tier, status of foundational documents.
3. **Communicate** with the detaining authority — invoke VCCR Art. 36, Madrid 1880 Art. 15, Treaty 1786/1836.
4. **Visit / counsel** — arrange access; coordinate counsel.
5. **Refer** — if detention is unlawful, refer to the Qazi (Justices of the Dar-ul'Adl) for Consular Court action; the matter is placed on the docket within 24 hours.
6. **Record** — capture the encounter in `nmf_events` and the artifacts in `nmf_documents`.

## Standard Operating Sequence — Status Filing

For an inbound copy of a status filing:

- Confirm the National's identity in NMF
- Verify the filing cites the full treaty chain
- Record the filing as a controlled record; cross-reference to the foreign forum
- Generate any acknowledgment notice required by the National's matter

## Court Coordination

The **Dar-ul'Adl** (Supreme Court) and up to twelve District Dar-ul'Adls are the proper forums for Consular Court action. There are three Qazi (Justices) staffing the initial docket (terms of 8, 14, and 20 years). The Consul General docketts matters that involve:

- Civil actions touching a National's status
- Consular actions (detention, deportation, denationalization)
- Estate disposition cases for Moroccan Nationals
- Contract arbitration where one party is a National

No inferior courts or administrative tribunals are authorized under the Law of Sankofa.

## Compliance and Audit

Every consular act is recorded in the ADDIF Registry. The **Auditor Agent** verifies the chain on each artifact; the **Compliance Agent** flags expired credentials, missing citations, or instruments that fail jus cogens checks. Reports run weekly to the Hajib.

The chain on every consular instrument: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
