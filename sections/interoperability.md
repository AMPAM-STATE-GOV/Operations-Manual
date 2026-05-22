# Interoperability

# ADDIF Interoperability and Diplomatic Exchange

The ADDIF Registry is designed to interoperate with other Moroccan State Governments, foreign states, financial institutions, and accredited international bodies — without surrendering AMPAM's sovereignty or the National's *jus sanguinis* standing. This section sets out the interoperability surface and the diplomatic exchange protocols. Every exchanged artifact carries the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Authority for Interoperability

The Treaty for the Moroccan State Union expressly anticipates exchange with other Moroccan State Governments: *"The Contracting Parties agree to form a Moroccan State Union which will be governed by principles set forth herein and any additional agreements made among them through mutual consent."* And the Law of Sankofa affirms (Right #29) *"the Right to Enter into Treaties, Agreements, Accords and Constructive Agreements with any and/or all States and Nations of the World, Earth and Cosmos."*

## Counterparty Classes

| Class | Examples | Channel |
|-------|----------|---------|
| **Moroccan State Government** | Other Provincial Governments under the Moroccan Empire | Direct ADDIF federation (state-to-state) |
| **Foreign State** | United States, Canada, Mexico, EU members | Diplomatic correspondence through the Hajib |
| **International Body** | UN bodies, OAS, ICJ | Formal submission through the Hajib |
| **Financial Institution** | Banks, custodians, exchanges | W-8BEN + trust documentation; ADDIF credential as identity layer |
| **Court** | Foreign court of competent jurisdiction | Consular Court referral or special appearance |
| **Officer** | Foreign agency officer | Notice package + treaty citation |

## Identity Layer

Three verifiable layers: **Institutional** — the WRW Trust LEI (`984500FFAO6C10CD8768`, on gleif.org), AMPAM LEI pending. **On-chain** — `ADDIFIdentity` soulbound ERC-721 on Polygon. **Document-level** — SHA-256 hash with Cert Server verification page (port 9100). A counterparty verifies in seconds — by LEI, token ID, or hash — without going through AMPAM staff.

## Diplomatic Exchange

For exchanges with foreign states or international bodies:

1. **Drafting** — the Hajib's office composes the diplomatic note; the Builder Agent assists, the Hajib signs
2. **Citation** — the note carries the treaty stack and the chain
3. **Delivery** — formal diplomatic channels (e.g., U.S. Office of Foreign Missions) or direct accreditation route
4. **Receipt and response** — recorded in `nmf_correspondence` and cross-referenced in `governance_documents`
5. **Escalation** — non-response or non-honoring is itself documented and may be referred to the ICJ track (per AMPAM's standing as referenced by Case No. 11 — France v. United States, Rights of Nationals of the U.S. in Morocco)

## Inter-State Federation

Other Moroccan State Governments may join the **Moroccan State Union** under the International Treaty for the Moroccan State Union. Each retains its sovereignty while joining in common causes. Federation at the technical layer is via the ADDIF federation protocol — registry-to-registry replication of public records, with private records kept local.

## Standards and Conformance

ADDIF adheres to the following standards where they do not conflict with AMPAM authority:

- **GLEIF LEI** for institutional identifiers
- **W3C DID and Verifiable Credentials** for the digital sigil (where compatible with soulbound-token semantics)
- **ISO 3166** for jurisdictional codes (with AMPAM as a non-ISO entity, identified by LEI)
- **IPFS / Filecoin** for content-addressed storage of public artifacts

## Compliance and Audit

The Auditor Agent verifies every interop artifact for chain integrity and citation completeness. The Compliance Agent monitors response and escalation timelines.

The chain on every interoperability artifact: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
