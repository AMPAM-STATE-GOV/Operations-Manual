# Digital Identity

# Digital Sigil and Identity Sealing

A National's **Digital Sigil** is the cryptographic seal that binds the National's recorded identity to the ADDIF Registry on-chain. Sealing is the act of minting that sigil. Once sealed, the sigil is non-transferable and persistent — the National's identity becomes part of the immutable record. Every sigil carries the chain on its face: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Underlying Instrument

The sigil is implemented as a **soulbound ERC-721 token** — the `ADDIFIdentity` contract deployed under AMPAM authority on Polygon. "Soulbound" means the token cannot be transferred, sold, or burned by anyone other than the controlling authority — it is bound to the National who is its subject, for life. One token per National. The contract enforces this at the protocol level.

The contract carries an embedded **LEI field** (one-time, immutable), tying the on-chain identity to AMPAM's institutional Legal Entity Identifier and, through that, to the Madrid 1880 / AMPAM / ADDIF Registry chain.

## Composition of the Sigil

Each sigil binds:

- **National identifier** — the ADDIF identifier assigned at registration
- **Pedigree class** — Matrilineal or Patrilineal status
- **Foundational hash** — SHA-256 fingerprint of the National's foundational document set (bonded birth record, pedigree affidavit, declaration of reclamation)
- **Star tier** — current Star (1 through 5)
- **AMPAM Seal** — the official Seal as cryptographic marker
- **Treaty chain** — Madrid Protocol 1880 → AMPAM → ADDIF Registry

A change in Star tier updates a metadata field on the token; the token itself never changes hands.

## Sealing Workflow

1. **Registration completes** — the National's record is created in the National Master File (NMF) with verified foundational documents.
2. **Hash assembly** — the registration handler computes the foundational hash from the verified document set.
3. **Mint** — the ADDIFIdentity contract mints the soulbound token to the National's controlling address. The mint transaction is recorded with the NMF identifier in `controlled_records`.
4. **Card issuance** — the Card PDF Server generates the National's credential card carrying the sigil's verification URL and QR code.
5. **Verification page** — the Cert Server (:9100) exposes a public verification page for the sigil, where any party can confirm authenticity by hash.

## Identity Protection

The sigil is the **non-derogable** anchor of the National's recorded identity. Because it is soulbound, it cannot be:

- Transferred to another party
- Pledged as collateral
- Re-minted in case of loss (a recovery process is defined separately and requires Hajib/Mufti sign-off)
- Subjected to denationalizing relabeling by any foreign jurisdiction

This aligns with the Law of Sankofa's affirmation that *"Status, Pedigree and National Standing being perpetually endured"* (Right #24) and the jus cogens prohibition against denationalization of indigenous peoples.

## Revocation and Reissuance

The sigil may be:

- **Suspended** — by the Compliance Agent if controlled records show fraud, but only via Hajib authorization
- **Restored** — after audit and Hajib sign-off
- **Reissued** — only on the death of the National, in which case the sigil is sealed in the `nmf_events` table as terminated and a memorial reference is preserved for *jus sanguinis* heirs

## Audit Trail

Every sigil event — mint, metadata update, suspension, restoration, termination — is recorded both on-chain (immutable) and in `nmf_events` (queryable). The Auditor Agent runs daily integrity checks comparing on-chain state to NMF state. Discrepancies are flagged immediately.

The chain on every sigil: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
