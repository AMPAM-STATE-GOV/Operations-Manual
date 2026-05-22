# Ai Governance

# AI Governance and Ethical Use Directive

The AMPAM platform uses AI as a technical collaborator — for drafting, validation, research, and routing — never as a substitute for human authority. This Directive sets the rules under which AI participates in system operations. Every AI-generated artifact carries the chain when published: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

## Foundational Posture

AI assists the System Architect and the human officials; it does not govern. Final authority on irreversible acts rests with the Wazir Al'Rais, the Hajib, the Mufti, and the Qazi, each within their constitutional scope. AI output is *drafted, reviewable, and overrideable* — never executed as a finality without human sign-off where the act is irreversible.

## Dual Mode Reasoning

AI operating on AMPAM matters distinguishes two modes and does not collapse them:

- **Mode A — Project Architecture**: internal systems, infrastructure, governance models, financial models, the trust hierarchy. AI may operate freely here, drafting designs, suggesting structure, simulating outcomes.
- **Mode B — External Reality**: foreign law, foreign institutions, foreign regulations, factual claims about external systems. AI must hold to factual accuracy and avoid speculation that would create false reliance.

Conflating these — projecting Mode A assumptions onto Mode B reality, or constraining Mode A design by Mode B limitations — is the most common failure mode, and the Directive flags it explicitly.

## Trust Liability Firewall

The AI must distinguish, in every reasoning chain, between:

- **Executor identities** (natural persons acting in office)
- **Trust entities** (WRW Trust, the National Trust, individual Foreign Grantor Trusts)
- **Public-facing entities** (AMPAM and its institutions, the ADDIF Registry)

Liability does not transfer between these unless explicitly defined. Each is modeled as a separate accounting and governance unit. The **WRW Trust** is private and never exposed publicly; AMPAM is the public face.

## The Seven Autonomous Agents

Automation runs through seven workers in `/opt/pdh/scripts/agent_workers.py` against the `task_queue` table (`FOR UPDATE SKIP LOCKED`): **Builder** (drafts documents/manual/templates), **Auditor** (validates records, checks chain compliance), **Research** (topical research, knowledge drafting), **StarAdvancement** (checks Star criteria, advances Nationals), **NoticeDelivery** (the standard notice package), **EstateValuation** (Estate value across seven wealth-ledger categories), **Compliance** (record audit, hash check, expiry flagging). All agents call the AI Proxy at port 9200 for multi-provider LLM routing.

## Gating

Every irreversible act — sigil mint, credential issuance, formal notice delivery, on-chain transaction, governance ruling — is **gated**: an agent may draft, but a human authority must sign off. Drafts are free; finality is approved. This Directive is enforced by the **Compliance Agent** which refuses to dispatch an act lacking the required signature.

## Knowledge Grounding

Builder, Research, and Auditor agents must search `knowledge_base` before drafting. Output lacking source citation (treaty, Constitution, or controlled record) is rejected by the Compliance Agent. This rule was added after early agent outputs contained hallucinated content — invented acronym expansions, off-topic templates — stored without grounding.

## Ethical Floor

No agent may act inconsistently with the Law of Sankofa or treaty stack, publish content that effects denationalization or violates jus cogens, modify a National's record without authorized human action, or communicate publicly on behalf of WRW Trust entities.

## Audit Trail

Every agent action is logged in `agent_runs` and `audit_events` with timestamp, inputs, outputs, and outcome. The Auditor Agent reviews these daily and reports anomalies to the Hajib.

The chain on every published AI-assisted artifact: **Madrid Protocol 1880 → AMPAM → ADDIF Registry.**

---
*Madrid Protocol 1880 → AMPAM → ADDIF Registry*
