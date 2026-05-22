# Tax Position

# Tax Position and Filing

This section sets out the AMPAM National's tax position with respect to foreign jurisdictions, and the filings used to assert and maintain that position. Every filing carries the chain: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## The Underlying Position

The AMPAM National holds *jus sanguinis* standing as an heir to the Moroccan Empire, naturalized into a foreign jurisdiction involuntarily and, upon reclamation under Madrid 1880 Article 15 ¶1, restored to protégé status. The tax position flows directly from this standing:

- The National is **not a tax-domiciled subject** of the foreign jurisdiction once protégé status is asserted on the record
- The National **is responsible** for accounting and reporting consistent with treaty obligations
- The National **does not surrender** allodial title or reversionary interests to foreign tax authority

This is a position taken under treaty, not under foreign statute, and it is asserted by filing — not by silence.

## Authority for the Position

The treaty stack: Treaty 1786/1836 (perpetual binding on United States agents), **Madrid 1880 Art. 15 ¶1** (protégé status for Moroccan nationals naturalized abroad), **Algeciras 1906** *Triple Principle* (Sovereignty, Territorial Integrity, **Economic Liberty and Equality**), VCCR 1963 (consular protection of economic interests), UNDRIP (economic self-determination).

## Core Filings (Star 4 Tools)

The Star 4 (Financial Operations) tier provides the standard tax filings:

| Filing | Purpose | Tool |
|--------|---------|------|
| **IRS Form 56** (Notice of Fiduciary) | Establishes the fiduciary capacity for the National's Estate | `form-56-generator.html` |
| **IRS Form 56-F** | Fiduciary for financial institutions | `form-56f-generator.html` |
| **W-8BEN** | Certifies non-resident-alien status for foreign-source income | (External form) |
| **Form 1041** | Trust income return for the National's Estate trust | `1041-x-generator.html`, `1041-es-v-generator.html`, `1041-k1-auto-filing-engine.html` |
| **Form 1099-OID** | Original Issue Discount recoupment | `1099-all-in-one-generator.html`, `1099-generator.html` |
| **Form 843** | Refund claim for improperly assessed taxes | `irs-form-843-refund-generator.html` |
| **Form 2848** | Power of Attorney for tax matters | `form-2848-generator.html` |
| **Form 8822-B** | Change of address / responsible party | `form-8822b-generator.html` |

## Filing Sequence

For a National advancing through Star 4:

1. **Establish fiduciary** — File Form 56 to put the IRS on notice of the National's Estate and the National's fiduciary capacity over it
2. **Certify status** — File W-8BEN for any income-producing relationships, citing the treaty chain in the certification block
3. **Open the Estate's accounts** — Use the 98-Series EIN (see `98-series-ein-wizard.html`) to establish the Estate as a foreign trust for tax purposes
4. **Report through 1041** — Annual trust return; preserves the trust's status as a non-domiciled entity
5. **Recoup with 1099-OID** — Where original-issue-discount recovery applies
6. **Refund through 843** — Where prior assessments were made under the involuntary naturalization

## Citation Block

Every filing includes a treaty citation block:

> *Filed under the authority of the Treaty of Peace and Friendship 1786/1836, Madrid Convention 1880 Article 15 ¶1, the General Act of Algeciras 1906, and the AMPAM Constitution (Law of Sankofa). Madrid Protocol 1880 → AMPAM → ADDIF Registry.*

## Recordkeeping

Each filing is recorded in `nmf_documents` with `doc_type='tax_filing'`, the SHA-256 hash, the receiving authority, and any response. The Auditor Agent verifies the citation block; the Compliance Agent flags filings nearing expiration or response deadlines.

The chain on every tax filing: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
