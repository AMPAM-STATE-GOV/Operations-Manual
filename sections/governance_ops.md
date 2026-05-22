# Governance Ops

# Governance Operations (Officials Manual)

This manual is for AMPAM officials operating the day-to-day governance of the Provincial Government — the **Provincial Divan**, comprising the Executive (Wazir Al'Rais), Legislative (Dalil Aziz, headed by the Seyaraha), and Judicial (Qazi, of the Dar-ul'Adl) branches, under the Law of Sankofa. Every governance act carries the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## The Three Branches

| Branch | Head | Composition | Term |
|--------|------|-------------|------|
| **Executive** | **Wazir Al'Rais** | Deputy, Secretariat (Dar-Al'Wazirate), Hajib, Mufti, Sutrah, others | 5 years; non-consecutive; max 3 lifetime |
| **Legislative** | **Seyaraha** (Head of the Dalil Aziz) | Matriarchal Dalil Aziz members | Seyaraha elected annually May 15 |
| **Judicial** | **Head Qazi** | Three Qazi initially; up to 12 District Dar-ul'Adls | Staggered 8/14/20-year terms |

## Executive Operations

The **Wazir Al'Rais** is the Supreme Officer and Spokesperson. The Secretariat (Dar-Al'Wazirate): Deputy Wazir Al'Rais, Wazir of the Baitul Mal (Treasury), **Hajib** (Minister of Foreign Affairs — oversees the Cadi, and the Rasm for National Standing / Trusts and Estates / Transportation), **Mufti** (Consul General), **Sutrah** (Defense — oversees Shariff), Nabi-Tasawwuf (Education), Wahy-Llham (Health and Family). The Wazir Al'Rais may veto a Dalil Aziz decision passed by less than 67% (2/3) affirmative.

## Legislative Operations

The **Dalil Aziz** has general oversight of all provincial government operations and is matriarchal in composition. It:

- Introduces, votes on, and presents bills to the Wazir Al'Rais
- Receives bills from within the body, from the Wazir Al'Rais, and from the body politic (Moorish Nationals)
- Oversees impeachment proceedings against any Executive, Dalil Aziz, or Judicial Officer
- Oversees the National Trust; appoints three Matrilineal Trustees

The **Seyaraha** manages administrative affairs, is the tie-breaking vote, and is elected annually on May 15 with affirmation by the Wazir Al'Rais and Head Qazi.

## Judicial Operations

The **Dar-ul'Adl** (Supreme Court) hears civil, criminal, family, consular, and contract matters. Initially three Qazi serve, with elections every 8, 14, and 20 years respectively (staggered, starting 2022). No inferior courts are authorized. Election requirements include Matrilineal National status for at least six years and lived presence in the Dominions for at least three consecutive years.

## Cross-Branch Recordkeeping

Every governance act — executive order (within constitutional bounds), legislative bill, judicial order — is a `governance_documents` row with SHA-256 hash, issuing branch/officer, and the chain. Constitutional articles live in `governance_articles`; treaty acts link to `treaty_obligations` and `treaty_participants`.

## Daily Officials Routines

Hajib's office opens cases routed from inbound correspondence and assigns to Rasm or Mufti. Mufti's office handles VCCR Art. 36 notifications and consular protection (see Manuals 011 and Officials 004). Cadi's office records deeds, tax assessments, and land conveyances. Sutrah coordinates with Shariff on defense/enforcement matters. The Dalil Aziz secretariat manages bills, votes, and impeachment proceedings. Qazi chambers docket matters, issue orders, and manage appeals.

## Constraints on Officials

The Law of Sankofa explicitly constrains every official against: personal gain, undue influence, influence peddling, foreign emoluments, bribes, unapproved office appointments, executive orders beyond constitutional limits, and personal oaths of allegiance.

## Audit and Reporting

The Auditor Agent verifies every governance artifact for chain compliance. The Compliance Agent monitors conduct against the Constitution's constraints. Weekly reports to the Hajib; monthly summaries to the Wazir Al'Rais and Seyaraha.

The chain on every governance instrument: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
