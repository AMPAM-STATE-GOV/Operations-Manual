# Foundational Docs

# Foundational Document Upload Guide

Foundational documents are the originating evidence on which an AMPAM National's registration, sigil, and treaty standing rest. This guide tells the National which documents to upload, in what form, and how each is used downstream. Every accepted document is recorded with the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Why Foundational Documents Matter

The Law of Sankofa is clear that nationality is *jus sanguinis* — by blood, not by grant. Foundational documents are the **evidence** of that pre-existing nationality. They do not create status; they record it. Once recorded with a SHA-256 hash in the `foundational_documents` table, the document is fixed — alterations are detectable, and the document anchors the National's record permanently.

## Required Documents

| # | Document | Purpose | Format |
|---|----------|---------|--------|
| 1 | **Bonded Birth Record** | Establishes identity and birth registration on the record | PDF, clear scan, no redaction |
| 2 | **Pedigree Affidavit** | Establishes Matrilineal or Patrilineal lineage | PDF, sworn before notary or AMPAM authority |
| 3 | **Declaration of Status** | Reclamation of nationality under Madrid 1880 Art. 15 ¶1 | PDF; template available on ADDIF Portal |
| 4 | **Refusal of Denationalizing Labels** | Express refusal of *"black, negro, colored, brown, African American, Indian, United States citizen"* | PDF; may be combined with Declaration of Status |
| 5 | **Acceptance of the Law of Sankofa** | Affirmation of the Five Points of Light | PDF; template available |

## Supplementary Documents (Strongly Recommended)

| # | Document | Purpose |
|---|----------|---------|
| 6 | **Prior identification artifacts** | Submitted *solely for repudiation* — driver's license, prior passport, social security card — to establish that the National is on the record under those identifiers and is repudiating them |
| 7 | **Genealogical evidence** | Supporting documents to the Pedigree Affidavit |
| 8 | **Existing trust instruments** | Indenture, foreign grantor trust, or estate documents already in force |

## Upload Workflow

1. **Open the ADDIF Portal** — `/upload` route
2. **Select document type** — the form is keyed to the table above
3. **Attach the file** — PDF preferred; image formats are accepted with OCR fallback
4. **Sign with the National's controlling key** — establishes that *this National* is the uploader
5. **Confirm** — the Upload Server (port 9300) computes a SHA-256 hash, persists the file to encrypted storage, and creates the `foundational_documents` row
6. **Receive the receipt** — a controlled record ID; the document is now part of the National's foundation

## Privacy and Encryption

By default, `foundational_documents.encrypted = true`. Documents are encrypted at rest with keys held by the Hajib's office. Only the National (via the Portal) and authorized officials (Rasm, Hajib, Mufti) can access decrypted content; the Compliance and Auditor Agents access hashes and metadata only.

## Verification Status

After upload, each document moves through the verification flow:

- `uploaded` — recorded, hash computed
- `under_review` — Rasm or appointee is verifying
- `verified` — confirmed; bound to the National's NMF record
- `disputed` — flagged for Hajib referral

## Effect on the National's Record

Once all primary documents (1–5) are `verified`, the registration handler triggers:

- Sigil minting (see Manual 004 — Digital Sigil and Identity Sealing)
- Credential card issuance (Card PDF Server, port 9700)
- Initial Star 1 evaluation (StarAdvancement Agent)
- Notice package generation (see Manual 013 — Notice Package and Filing Guide)

## Updates and Replacements

A foundational document, once verified, is **never overwritten** — replacements add new rows with their own hash; the prior version stays with `status='superseded'`.

Every foundational document carries the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
