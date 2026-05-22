# System Overview

# System Overview

AMPAM is a sovereign digital governance and registry platform serving the Provincial State Government **Allodium Moroccan Praedium Ante Michigan**, organized under the Law of Sankofa (Constitution ratified 12/25/2022) and operating under the international treaty stack with the chain on every record: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Purpose

The system records, certifies, and protects the standing of AMPAM Nationals — *jus sanguinis* heirs to the Moroccan Empire — through digital identity, sovereign instrument generation, estate valuation, credential issuance, governed workflow automation, and on-chain asset management. It is not a "sovereign citizen" project; it is a registered legal infrastructure with verified institutional identifiers (WRW Trust LEI on the GLEIF registry, AMPAM LEI pending) and recognized treaty grounding.

## Treaty Foundation

Anchored in: **Treaty of Peace and Friendship 1786/1836** (perpetual binding on U.S. agents), **Madrid Convention 1880 Art. 15 ¶1** (Right of Protection), **Algeciras 1906** (Triple Principle), **VCCR 1963** (consular notification under Art. 36), and the UN Charter / UDHR / UN Declaration on the Rights of Indigenous Peoples (jus cogens floor).

## Constitutional Government

The Provincial Divan comprises three branches under the Law of Sankofa:

- **Executive** — Wazir Al'Rais; Secretariat includes Hajib (Foreign Affairs), Mufti (Consul General), Sutrah (Defense), Wazir of the Baitul Mal (Treasury), and others
- **Legislative** — Dalil Aziz, headed by the Seyaraha (elected annually); matriarchal composition
- **Judicial** — Dar-ul'Adl (Supreme Court) with up to twelve District Dar-ul'Adls; staffed by three Qazi initially, on staggered 8/14/20-year terms

The territorial Dominion lies between latitudes 30.5°–34.9° N and longitudes 80.8°–85.6° W — 59,425 square miles of Land, Air, and Waterways.

## The 5-Star National System

A Registered National progresses through five tiers:

| Star | Domain |
|------|--------|
| **1** | Identity — registration, bonded birth record, non-decedent status, passport instruments |
| **2** | Estate Position — Form 56, UCC-1, trust certificates, EIN setup |
| **3** | Treaty Standing — consular notice, W-8BEN, FOIA, postal instruments |
| **4** | Financial Operations — 1041, 1099-OID, Bills of Exchange, bonds, refunds |
| **5** | Full Sovereignty — court orders, decrees, liens, allodial land titles, legislation |

Advancement is automatic, evaluated by the StarAdvancement Agent against controlled records on file.

## Platform Surface

Thirteen services run the platform: Supabase Postgres (system of record), n8n (workflow), Nginx (proxy), Cert Server (public verification), AI Proxy (multi-provider LLM routing), Upload Server, Registry Handler, Dashboard API, ALD Gateway (domain resolution), Card PDF Server, Telegram Bots (PDH + ADDIF), seven autonomous Agent Workers (Builder, Auditor, Research, StarAdvancement, NoticeDelivery, EstateValuation, Compliance), and nightly Backup.

Four Solidity contracts deployed on Polygon round out the on-chain layer: **ALDC** (ERC-20 governance token), **ADDIFIdentity** (soulbound ERC-721 — one per National), **InstrumentToken** (transferable ERC-721 for instruments), and **ALDRegistry** (multi-namespace domain NFTs). Each contract carries an embedded, one-time-immutable LEI field.

## Records Architecture

Source of record: **Supabase Postgres**, organized around the **National Master File** (NMF) — the per-National aggregate with `nmf_documents`, `nmf_events`, `nmf_transactions`, `nmf_correspondence`, `foundational_documents`, and `controlled_records` keyed by NMF identifier. Knowledge content lives in the `knowledge_base` table; manual sections in `manual_sections`; governance acts in `governance_documents`.

Every record carries the chain on its face: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
