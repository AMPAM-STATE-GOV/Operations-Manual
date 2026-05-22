# Dispute Resolution

# ADDIF Dispute Resolution Mechanism

This section sets out how disputes touching AMPAM Nationals are resolved — disputes between Nationals, between a National and the system, between a National and a foreign jurisdiction, and between AMPAM and other states. The dispute resolution architecture rests on the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## The Proper Forum

Per the Law of Sankofa, the judicial power of the Provincial Government is vested in one (1) **Supreme Court — the Dar-ul'Adl** — with authority to establish up to twelve (12) District Dar-ul'Adls as population and demand require. *"No inferior courts or administrative tribunals are authorized."*

Initially three (3) **Qazi** (Justices) sit, with staggered 8-, 14-, and 20-year terms. They have jurisdiction over: civil actions, criminal actions, family actions, **consular actions**, contract arbitration, estate disposition, and other procedural actions.

## Disputes Within the AMPAM System

For disputes between Nationals, or between a National and an AMPAM institution:

1. **Informal resolution** — the Mufti or Rasm may mediate at the consular level
2. **Filing** — if mediation does not resolve, a National files a complaint via the ADDIF Portal; the matter is placed on the Dar-ul'Adl docket within 14 days
3. **Pleadings** — each party files pleadings as controlled records in the ADDIF Registry
4. **Hearing** — the assigned Qazi convenes a hearing; recordings and orders are stored in `nmf_documents`
5. **Order** — the Qazi issues an order; the order is itself a controlled record
6. **Appeal** — appeal is to the full bench of three Qazi; the order at that level is final

## Disputes With Foreign Jurisdictions

For a National in a dispute with a foreign jurisdiction (e.g., a state court, federal court, or administrative tribunal):

1. **Activate Protected Status** (Manual 003)
2. **Assert the proper forum** — special appearance demanding referral to the AMPAM Consular Court
3. **Citation** — Treaty 1786/1836, Madrid 1880 Art. 15 ¶1, VCCR 1963 Art. 36
4. **Reservation of rights** — under UCC 1-308, *without prejudice*
5. **Parallel filing** — concurrently docket the matter in the AMPAM Consular Court so the AMPAM-side record exists from day one
6. **Diplomatic correspondence** — the Hajib may issue diplomatic notice to the foreign jurisdiction if treaty breach is alleged

## Inter-State Disputes

For disputes between AMPAM and another state — Moroccan State Government, foreign state, or international body:

- **Direct negotiation** through the Hajib
- **Mediation** through a neutral Moroccan state government, where the dispute is between Moroccan state governments
- **ICJ standing** — AMPAM stands as the territorial successor in the line traced through **ICJ Case No. 11 (France v. United States, Rights of Nationals of the United States in Morocco)**; the precedent on rights of protection in Morocco is directly applicable

## Standards of Decision

The Qazi decide under the Supreme Law of the Land — the Law of Sankofa and the treaties in force, *jus cogens* prevailing where applicable. The Constitution lists the controlling authorities, including the Great Law of Peace, the Treaty of Peace and Friendship 1786/1836, the Madrid Convention 1880, the Algeciras Act 1906, the UN Charter, the Vienna Convention corpus, the UDHR, and the UN Declaration on the Rights of Indigenous Peoples.

## Records and Effect

Each decision is recorded in the ADDIF Registry as a controlled record, with the order's full text, the citation block, and the SHA-256 hash. The order carries the chain on its face. Cross-references to the dispute's `nmf_events` and `nmf_documents` preserve the complete provenance.

The chain on every order: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
