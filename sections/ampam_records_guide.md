# Ampam Records Guide

AMPAM Records is the digital instrument administration authority. Every instrument submitted through the system flows through the AMPAM Records pipeline.

THE PIPELINE:
1. INTAKE — instrument is cataloged with a unique number (AMPAM-REC-YYYY-NNNN)
2. VALIDATE — structure check against CER Article 12 requirements, validation score 0-100, risk assessment
3. REGISTER — controlled record created with SHA-256 hash and controller ID
4. STORE — document uploaded to IPFS with permanent content-addressed storage
5. MINT — InstrumentToken NFT created on Polygon with 2.5% perpetual royalty

REVENUE AT EVERY STEP:
Each stage generates an ALDC fee. Every NFT transfer generates a 2.5% royalty forever through EIP-2981.

The AMPAM Records portal at /records.html provides full pipeline visibility: catalog, validation details, mint queue, royalty ledger, and engine status.

The Record Engine runs as an autonomous service, polling for new instruments and processing them through the pipeline automatically.

Officials see a simplified view in the Gov Dashboard AMPAM Records tab. The full pipeline is visible in the standalone portal.

Madrid Protocol 1880 → AMPAM → ADDIF Registry

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
