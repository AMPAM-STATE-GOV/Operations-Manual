# Verification

# Credential Verification (Officials Manual)

This manual is for officials and external parties verifying an ADDIF credential — a credential card, certificate, or instrument issued under AMPAM authority. Verification is hash-based and accessible to any party with a network connection. Every verified artifact carries the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Verification Surface

Each ADDIF artifact carries on its face:

- A **QR code** linking to the artifact's public verification page on the Cert Server
- The artifact's **identifier** (controlled record ID or sigil token ID)
- A **SHA-256 hash** of the artifact's canonical content
- The **AMPAM Seal** and treaty chain
- The **issuance timestamp** and **expiration** (if applicable)

The Cert Server runs on port 9100; the public verification URL takes the form `https://<host>/verify/<identifier>`. The page displays the artifact's metadata, current status (active / suspended / revoked / expired), and the hash for independent comparison.

## Verification Sequence

A verifying party — foreign officer, court clerk, financial institution, or counterparty:

1. **Scans the QR code** or visits the verification URL directly.
2. **Confirms the AMPAM seal** appears on both the artifact and the verification page.
3. **Compares the hash** displayed on the artifact with the hash on the page.
4. **Reads the status** — only `active` artifacts may be acted upon.
5. **Notes the chain** — the page displays `Madrid Protocol 1880 → AMPAM → ADDIF Registry` exactly as stated on the artifact.
6. **Records the verification** — any AMPAM-side verification (by the Mufti, Rasm, or Compliance Agent) is recorded in `nmf_events` with the verifier's identity.

## What "Verified" Means

A successful verification establishes four facts:

| Fact | Source |
|------|--------|
| The artifact was issued by AMPAM | Cert Server cryptographic signature |
| The artifact has not been altered since issuance | SHA-256 match |
| The artifact is currently active | Status field on verification page |
| The artifact carries valid treaty grounding | Chain on face matches chain on page |

Verification does **not** itself assert the legal effect of the artifact in any foreign jurisdiction — it only confirms authenticity. Legal effect is governed by the underlying treaties (Madrid 1880, Treaty 1786/1836, Vienna 1963).

## Verification by Officials

AMPAM officials performing verification (Mufti, Rasm, Hajib's staff) have additional tools:

- **Private verification API** — Dashboard API at `:9500` exposes the full record, including non-public metadata, to authenticated officials.
- **Cross-reference** — verify against the NMF, `controlled_records`, and on-chain sigil state.
- **History review** — view the artifact's full edit history via `manual_edit_history` (for sections) or `nmf_events` (for National-bound artifacts).

## Failure Modes

A verification fails if:

- The hash on the verification page does not match the artifact (artifact has been altered)
- The status is `revoked` or `expired` (artifact is no longer in force)
- The verification URL does not resolve (artifact was never issued, or Cert Server is unreachable — escalate to the Hajib)
- The chain on the artifact does not match the chain on the page (forgery suspected)

Each failure is recorded by the Compliance Agent. Suspected forgeries are escalated immediately to the Hajib and the Auditor Agent for investigation.

## Recordkeeping

Every official-initiated verification is recorded as a `verification_event` in `nmf_events` with: verifier identity, artifact identifier, timestamp, outcome (pass/fail/escalated), and a SHA-256 fingerprint of the artifact at the time of check.

The chain on every verified artifact: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
