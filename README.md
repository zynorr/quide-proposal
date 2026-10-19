# QuIDE

**Write, test, and ship Qubic contracts from your browser.**

QuIDE is a cloud development platform for Qubic C++ smart contracts: hosted browser workspaces, one-click isolated devnets, integrated compile/test/verification, shareable review environments, and CI. Zero local setup - no Linux box, no AVX2 CPU, no 24-32 GB RAM requirement, no hand-provisioned test node.

> **Status: pre-build.** This repository is the incubation proposal and its evidence base. The hosted product is not live yet; see [docs/05-validation-traction.md](docs/05-validation-traction.md) for validation status and [demo/](demo/) for the concierge pilot walkthrough.

## Why it matters

- Qubic's official local dev environment requires **Linux x86-64 + AVX2, ≥24 GB RAM (≥32 GB full stack), 8+ cores, 25-50 GB/day disk writes** - official docs call it *"a real dev environment, not a laptop toy"* and tell non-Linux users to rent a VPS. macOS and Windows are not supported for the recommended path. **[V]** - [docs.qubic.org/developers/dev-kit](https://docs.qubic.org/developers/dev-kit)
- Team and hackathon isolation requires **manually provisioned dedicated test nodes** - *"contact the hackathon organizers"*. **[V]** - [github.com/qubic/qubic-hackathon](https://github.com/qubic/qubic-hackathon)
- Qubic's own grants repository still lists an **unclaimed RFP: "Online Code Editor for C++ Smart Contracts"**. **[V]** - [github.com/qubic/grants](https://github.com/qubic/grants)
- Hackathons are the main developer funnel - **1,654 participants / 265 teams** in one December 2025 event - and every event re-solves the same missing product by hand. **[V]** - [lablab.ai case study](https://lablab.ai/ai-articles/qubic-ai-hackathon-case-study)

## What QuIDE does (MVP)

1. **Browser workspace** - current `qubic/core` checkout, Monaco/VS Code editor, starter templates, terminal, compile + GoogleTest + `qubic-contract-verify` in one click.
2. **One-click devnet** - isolated private testnet per project (faucet, funded identities, RPC/WS), snapshot/restore, teardown; replaces the manual `deploy.sh`/`cleanup.sh` cycle.
3. **Deploy + observe** - deploy into your devnet, live qlogging event stream, CLI console, state view.
4. **Share + CI** - team workspaces, reviewer links, GitHub push → compile/tests/verify pipeline.
5. **Hackathon/education mode** - pre-warmed seats and sponsor-funded credits.

**Non-goals:** no token, no new chain/L1 features, no AI chatbot core, no bypass of mainnet governance (PR → proposal → IPO unchanged).

## How to try it

Not publicly available yet. Until the hosted beta, the reproducible **concierge pilot** (manual isolated devnet provisioning using the official AIO dev-kit) is documented in [demo/](demo/) - we run it with design partners during validation.

## Who is building it

Two committed founders - a systems/infrastructure engineer and a product/full-stack engineer; see [docs/01-team.md](docs/01-team.md).

## Repository map

| Path | Contents |
|---|---|
| [docs/00-summary.md](docs/00-summary.md) | One-page summary: problem, user, why Qubic, ask, milestones, return |
| [docs/01-team.md](docs/01-team.md) | Roles, experience, ownership, commitment |
| [docs/02-problem-icp.md](docs/02-problem-icp.md) | Problem & ideal customer profile |
| [docs/03-why-now-why-qubic.md](docs/03-why-now-why-qubic.md) | Why now, why Qubic |
| [docs/04-product-demo.md](docs/04-product-demo.md) | User flow, MVP scope, demo, technical risks |
| [docs/05-validation-traction.md](docs/05-validation-traction.md) | Evidence, validation plan, gates |
| [docs/06-market-gtm-competition.md](docs/06-market-gtm-competition.md) | Market, GTM, competition |
| [docs/07-business-model-pricing.md](docs/07-business-model-pricing.md) | Business model & pricing |
| [docs/08-return-to-incubation.md](docs/08-return-to-incubation.md) | Return proposal |
| [docs/09-milestones-budget.md](docs/09-milestones-budget.md) | Milestones, acceptance criteria, budget |
| [docs/10-risks-security.md](docs/10-risks-security.md) | Risks, security assumptions, audit plan |
| [data/](data/) | Assumptions, evidence, full research report |
| [demo/](demo/) | Concierge pilot & planned demo artifacts |

**Evidence tags used across docs:** **[V]** verified against a primary source (link given) · **[I]** inferred · **[U]** unvalidated hypothesis.
