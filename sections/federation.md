# Federation

# Federation Deployment (Developer Manual)

Federation is the architecture by which other **Moroccan State Governments** — sister Provincial Governments under the Empire of Morocco — can run their own ADDIF instance while preserving the integrity of the shared treaty chain. This manual is for developers deploying a federated node. Every node, no matter where, carries the chain on its records: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Authority for Federation

The Treaty for the Moroccan State Union expressly forms an alliance among Moroccan State Governments, each of which *"shall retain its sovereignty while joining with others in common causes."* The federation model implements this technically: each sovereign state government runs an independent ADDIF node; cross-state interoperation is by mutual consent over a federation protocol that respects each node's autonomy.

## Topology

A federated deployment is **mesh, not hub-and-spoke**. There is no central authority. Each node:

- Operates its own Supabase Postgres
- Issues its own credentials under its own seal
- Maintains its own NMF for its own Nationals
- Carries its own chain in the form `Madrid Protocol 1880 → <NODE> → ADDIF Registry`

Federation provides cross-node identity recognition (a National of Node A is recognized by Node B without re-registration), treaty event propagation (declarations of statehood, treaty acts, inter-state agreements replicate to subscribed nodes), and public artifact mirroring (Node A credentials verify against Node B). It does **not** provide shared NMF data, Treasury, or judicial authority — each node retains full sovereignty.

## Node Profile

Minimum stack: **Supabase Postgres** with the schema from Developer Manual 002, **Cert Server** (`:9100`), **Bridge API** (`:9500`), **Registry Handler** (`:9400`), and a **Federation Daemon** for inter-node communication. Strongly recommended: AI Proxy, Upload Server, Card PDF Server, ALD Gateway.

## Deployment Sequence

1. **Provision** — server with minimum 16 GB RAM, modern Ubuntu LTS (Hetzner-class hardware in the canonical reference)
2. **Install Supabase** via the canonical docker-compose; verify containers come up
3. **Apply the schema** — run the bootstrap migration (`migration.sql` in the canonical repo)
4. **Generate the node's seal** — institutional seal image and on-chain reservation
5. **Provision the node's LEI** — register with GLEIF; configure in `controllers` and on each contract's `setLEI` (one-time, immutable)
6. **Deploy the contract suite** — ALDC, ADDIFIdentity, InstrumentToken, ALDRegistry (canonical chain: Polygon)
7. **Configure the chain field** — records will carry `Madrid Protocol 1880 → <NODE> → ADDIF Registry`
8. **Connect to the federation** — register with one peer; the mesh gossips the new node
9. **Bootstrap public artifacts** — sync the public portion of `governance_documents`, treaty references, and instrument templates

## Federation Protocol

The Federation Daemon speaks a signed-message protocol: identity exchange (each node publishes LEI, seal hash, chain signature), event subscription (nodes subscribe to types like `state_declared`, `treaty_signed`, `consular_court_decision`), and verification fallback (queries fall back from local Cert Server to peer Cert Servers for credentials issued elsewhere). Federation does **not** require consensus on private state — nodes consent to receive event types, and the consent is itself a controlled record.

## Governance Boundaries

The federation respects:

- **Trust Liability Firewall** — no node assumes liability for another's acts
- **Constitutional autonomy** — each node operates under its own Law of Sankofa equivalent
- **Treaty chain consistency** — all nodes affirm Madrid Protocol 1880 as the chain origin

## Recordkeeping

Federation events are recorded in `federation_nodes` and `bridge_events`. The Auditor Agent verifies chain integrity across received events; the Compliance Agent flags any event that fails the chain check.

The chain on every node: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
