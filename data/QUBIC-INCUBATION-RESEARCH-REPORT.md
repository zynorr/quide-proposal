# Qubic Incubation Program — Research Report

**Candidate project identification for the Qubic Incubation Program**
Prepared: October 2026 · Method: primary-source research (official sites, docs, GitHub repos, ecosystem directory, hackathon material)
Evidence tags: **[V]** = Verified against primary source (URL given) · **[I]** = Inferred from cited evidence · **[U]** = Unvalidated / hypothesis, must be tested before committing

Sources index at the end (Appendix A). Every material claim in this report is traced to a source.

> **Update (Oct 2026):** §9 and §13 revised per team decision: the final ask is **$30K / ~12 weeks** with trimmed scope. The research-stage $115K full-feature estimate is superseded (revision note in §9; current plan in `docs/09-milestones-budget.md`).

---

## 1. Executive Verdict

**CONDITIONAL GO.**

One candidate clears the bar: **QuIDE** — a **cloud development platform for Qubic C++ smart contracts** (hosted browser workspaces + one-click ephemeral devnets + integrated verification/testing/CI) — the production-grade, for-profit version of the ecosystem's own long-unclaimed RFP "Online Code Editor for C++ Smart Contracts." [V]

Score: **82/100** (section 5.1). The deduction is almost entirely in commercial-viability evidence (5/10): the pain is verified and officially acknowledged, the product gap is verified, but willingness-to-pay in a young ecosystem is a hypothesis, not yet a fact. That is exactly what the pre-application validation plan (section 11) is designed to falsify cheaply.

**Go conditions (all three must pass before writing the application):**

1. **Demand gate** — ≥10 structured interviews with Qubic hackathon participants, Nostromo-track teams, and contract developers; ≥3 non-binding pilot commitments at a stated price.
2. **Non-compete gate** — written signal from Qubic Foundation/QCT (Discord `#dev` or incubation team) that no official hosted IDE/devnet product is on the near-term roadmap, and positive interest in the RFP being executed commercially.
3. **Concierge gate** — manually provision isolated devnets for 3–5 real teams using the official AIO kit automation; require ≥50% of teams to keep using them over 3+ weeks and median time-to-first-contract-deploy under 30 minutes.

Fallback if the demand gate fails: the "OpenZeppelin-equivalent C++ contract library" (section 5, candidate #2) executed as a hybrid grant + incubation component, or pivot to the runner-up payments lane (candidate #15) only with fresh evidence.

---

## 2. Recommended Project

**Name: QuIDE** (Q + IDE, reads as "guide") *— adopted as the project name; domain and trademark availability still to be verified. Do not reuse "Qubic Smart Contract Studio" — a hackathon repo already uses it [V].*

**Tagline:** *Write, test, and ship Qubic contracts from your browser.*

**One sentence:** A browser-based, zero-install workspace where a developer can write, compile, test, and deploy a Qubic C++ smart contract to an isolated private devnet in minutes, with the same toolchain the core team uses (core-lite, GTest harness, contract-verify, CLI, qlogging) — priced as a freemium SaaS for individuals and teams, with hackathon/education sponsorship as the acquisition channel.

**Why this and not something bigger:** Qubic's binding constraint is external smart-contract developer throughput. The chain infrastructure is done (ticks, QPI, contracts, indexers, bridges, wallets, DEXs — all live or in QA [V]). The remaining bottleneck is the step *before* a contract reaches the core repo: the develop → compile → test → simulate → iterate loop, which today requires a Linux AVX2 machine with ≥24 GB RAM, writes 25–50 GB/day, and for team/hackathon isolation requires a hand-provisioned dedicated test node from the organizers [V]. That is a verified, officially acknowledged bottleneck with an official open RFP — and no production product in the ecosystem solves it [V].

---

## 3. Evidence of the Problem

**3.1 The officially requested product does not exist.**
The Qubic grants repository still lists the RFP *"Online Code Editor for C++ Smart Contracts"*: a web-based IDE with syntax highlighting, debugging tools, live contract simulation, and deployment from the IDE — "without the need for local installations," explicitly to "lower the barrier to entry and accelerate the development process." [V: grants RFPs] The repo shows **0 issues and no claimed/fulfilled RFP**; the ecosystem directory (~47 entries, Oct 2026) contains **no online IDE or hosted dev-environment product** [V: ecosystem directory; GitHub grants repo].

**3.2 The official local path excludes most developers by hardware and OS.**
The recommended AIO Qubic Dev Kit requires: Linux x86-64 with AVX2, Ubuntu 24.04 recommended; **≥24 GB RAM (≥32 GB with explorer)**; 8+ CPU cores; **~25–50 GB/day disk writes** at 1 s ticks. Official wording: *"This is a real dev environment, not a laptop toy"* and *"Not on Linux? Spin up a dev VPS."* macOS and Windows are **not supported** for the AIO path. [V: docs.qubic.org/developers/dev-kit + setup-environment] The lighter core-lite local testnet still needs **16 GB RAM** [V: github.com/qubic/core-lite]. So a Windows/macOS laptop developer — the majority audience for onboarding — cannot run the sanctioned one-command environment at all; the official answer is "rent a VPS."

**3.3 Team/hackathon isolation is hand-provisioned and manual.**
Official testnet docs: the public testnet is for *"general development and testing"*; dedicated nodes with *"isolated environments for testing smart contracts without interference"* are only *"may be provided"* for projects or hackathons. [V: docs testnet-resources] The hackathon hub instructs teams to *"contact the hackathon organizers to get access"* to an SSH node, then run `deploy.sh`, and after **every** contract change run `cleanup.sh` then redeploy. [V: github.com/qubic/qubic-hackathon] There is no self-service path.

**3.4 The demand is quantified and recurring.**
Qubic runs recurring hackathons as its main external developer funnel: Madrid 2025 — 127 hackers, 27 teams, 24 pitching, first-ever testnet contract deployments at an event, €80K prize pool [V: Qubic blog recap]; LabLab "Raise Your Hack" (Paris 2025) [V]; "Hack the Future" fully online Dec 5–7, 2025 — **1,654 enrolled, 265 teams, 96 AI apps** [V: lablab case study]. Each event needed per-team nodes provisioned by hand; every event is a rerun of the same missing product. A community project (Latio's qforge/qubicdev.com) already provides a faucet and general testnet interaction [V], confirming that self-service test tooling attracts usage — it just stops short of an IDE/devnet workspace.

**3.5 Prior art attempts confirm the gap rather than disprove it.**
Hackathon teams have repeatedly attempted browser IDEs: "Qubic Smart Contract Studio" (Monaco editor, one-click deploy — unmaintained hackathon repo, Nov 2025) [V] and "QubiLearn" (lablab, Jul 2025 — learning platform with live editor) [V]. None became a maintained product; none appears in the ecosystem directory. The pattern "official RFP + repeated hackathon attempts + zero production product" is the strongest possible pre-build signal short of paying customers.

**3.6 The pain extends to the core workflow, not just setup.**
Contract development involves GTest unit tests, the `qubic-contract-verify` restriction checker, qlogging event streams, and eventually a PR to `qubic/core` [V: lifecycle + testing docs]. These are all CLI/file-tree workflows with no integrated web experience. CI — running the tests automatically on every push — has no hosted story at all [I: no CI tooling found in ecosystem audit].

---

## 4. Existing-Product Audit

Complete audit of the ecosystem directory (~47 entries) + GitHub org (77 repos across 3 pages) + searches, as of Oct 2026:

| Lane | Product(s) | Status | Verdict for our candidate |
|---|---|---|---|
| Contract deploy/interact UI | **qforge** (Latio) + qubicdev.com faucet/CLI/tester | In Development (Oct 2025) | Adjacent, does not compile/run/simulate contracts; potential integration partner [V] |
| SC audit/test (AI) | **qbuild** (Kairos Tek, Raise-Your-Hack winner) | Live, Incubation | Audit-focused, not a dev environment; candidate integration, not competitor [V] |
| Explorer + "all-in-one" tools | **Qubihub** (community) | In Development | Closest timing risk; roadmap = explorer + contract tools + utilities; watch closely [V] |
| Desktop client / interact | **Qubic.NET.Toolkit** (official .NET) — wallet, tx, contract browser, DeFi suite | Beta | Windows/macOS/Linux desktop interaction; no IDE/devnet [V] |
| Local environment | **AIO Dev Kit** (official, replaced archived Madrid kit 2026-07-22), **core-lite** (official) | Live | The substrate our product hosts; core-lite's 16 GB requirement still excludes laptops; AIO is Linux-only [V] |
| Contract library std. | **OpenZeppelin-equivalent RFP** | RFP open, no product | Adjacent candidate (#2); complementary templates can seed our gallery [V] |
| Event/webhook/automation | **Easy Connect** (NevTrace) | Live, Incubation, freemium | Verified covered — eliminated lane [V] |
| Indexing/data | core-bob, go-archiver-v2, archive-query-service, stats-service, Core Lite | Live | Covered — eliminated lane [V] |
| Analytics | Qubic Metrics, myLedger, whale alerts | Live | Covered — eliminated [V] |
| Wallets/hardware | Web/extension/mobile, MetaMask Snap, HASHWallet, Onyze custody, **Ledger app** (live Jul 2026) | Live | Covered — eliminated [V] |
| Bridges | QBridge (Vottun, ETH, IPO epoch 205, 2-of-3 multisig), SolanaBridge | Live / Testnet | Covered — eliminated [V] |
| DEX/AMM/launchpad | QX, QubicSwap, QSwap, Qubictrade, QXBoard, **Nostromo** (official launchpad), **QIP** (ICO contract) | Live / upgrading | Covered — eliminated [V] |
| Payments | **QPayhub** (x402 settlement + oracle price feed, in-core, community dev), Banxa ramps | In progress | Lane contested; monitor as fallback #15 [V/I: QPayhub test-status notes suggest pre-completion] |
| Education | Qubic Academy, docs, videos | Live | Marketing channel for our product, not a competitor [V] |

**Conclusion:** the "develop/test/deploy contract in the browser with an isolated environment" lane is empty. Every other verified gap that a for-profit product could occupy is either taken (alerts, indexing, analytics, wallets, bridges, DEX) or lacks any demand evidence (lending, stablecoin, name service — section 5).

---

## 5. Candidate Comparison

### 5.1 Scorecard for the recommended project (weights per brief)

| Criterion | Weight | Score | Justification |
|---|---|---|---|
| Evidence of a real, consequential problem | 25 | **23** | Official open RFP + official docs barriers + manual per-team provisioning at recurring hackathons [V] |
| Differentiation from existing solutions | 20 | **16** | No production product; partial overlap with qforge/Qubihub/qbuild; hackathon attempts unmaintained [V] |
| Technical feasibility on Qubic | 15 | **13** | All components exist (core-lite, AIO compose, GTest harness, contract-verify, CLI, qlogging); hard part is multi-tenant infrastructure, not invention [V/I] |
| Fit with incubation objectives / impact | 15 | **13** | Directly grows contract-developer throughput = ecosystem's #1 goal; matches official RFPs and "Developer tools" wishlist [V] |
| Commercial viability and evidence of demand | 10 | **5** | Cloud dev environments are a proven SaaS category elsewhere [I]; Qubic willingness-to-pay is [U] — the main risk |
| Feasibility of a testable MVP | 10 | **9** | Time-to-first-deploy, workspace activation, CI minutes — all objectively measurable from signup logs |
| Long-term sustainability | 5 | **3** | Durable niche but small at current dev counts; revenue scales only if SC adoption scales |
| **Total** | **100** | **82** | **CONDITIONAL GO** |

### 5.2 All candidates considered (15) with elimination reasons

1. **Cloud dev workspace / online IDE + devnets** — **RECOMMENDED.** (Evidence: §3.)
2. **OpenZeppelin-equivalent C++ contract library** — official RFP, genuinely missing [V]; eliminated as primary because a base library is a public good with no direct revenue path → fits the **grants** program, not incubation economics. Recommendation: keep as a component (template gallery) or respect the RFP as a separate grant.
3. **Gnosis-like multisig UI on MSVAULT** — official RFP [V]; but MSVAULT contract is live and partially exposed by Qubic.NET.Toolkit and community tool pages [V]; weak monetization for a security-critical UI used by a handful of treasuries. Eliminated.
4. **Lending protocol** — on the grants wishlist ("Lending Protocols") [V]; but **no demand evidence exists**: no live lending anywhere on Qubic, and market depth is tiny (point-in-time DEX TVL in the low tens of thousands of USD when checked; [U] due to volatility) — a money market's fees cannot cover an IPO, audits, and liquidation infra at this depth. Eliminated for lack of evidence, not lack of importance.
5. **Stablecoin / VUSD-style credit** — the 2024 Valis concept never shipped [V]; fiat on-ramps are already being handled at the core level (Banxa integration operating) [V]; heavy regulatory load. Eliminated.
6. **Contract execution-fee reserve monitoring/ops console** — lifecycle docs explicitly warn contracts stop when the reserve hits zero and say monitor it regularly [V]; but the addressable market is ~35 contracts, QReservePool covers part of the reserve mechanics on-chain [V], and willingness-to-pay is unproven. Eliminated (too small).
7. **Runtime security monitoring / incident response for contracts** — no dedicated product [I]; but again a ~35-contract market, overlapping qbuild (pre-deploy) and Easy Connect (generic alerting). Eliminated (weak demand evidence).
8. **Event monitoring / webhooks / no-code automation** — **taken**: Easy Connect is Live and Incubated, freemium, covering event subscriptions/webhooks [V]. Eliminated.
9. **Historical indexing / query APIs** — **taken**: core-bob, go-archiver-v2, archive-query-service, qubic-stats-service, Core Lite [V]. Eliminated.
10. **Analytics dashboards** — **taken**: Qubic Metrics (Incubated), myLedger, whale-alert bots, QXBoard [V]. Eliminated (also on the brief's generic-idea ban list).
11. **Hardware wallet** — **taken**: official Ledger app live since July 2026 [V]. Eliminated.
12. **Cross-chain bridge** — **taken/in progress**: QBridge (Vottun) live on ETH; Solana bridge in QA [V]. Eliminated.
13. **Launchpad / token issuance / crowdfunding** — **taken**: Nostromo official launchpad (upgrading), QIP ICO contract in core [V]. Eliminated.
14. **Name service** — grants wishlist [V]; but docs treat QNS as a coding example only [V], standalone NS revenue is negligible in small chains (ENS-style economics need volume), and it is a feature of a wallet/explorer rather than a company. Eliminated (revisit as feature).
15. **Streaming payments / payroll** — grants wishlist ("feeling-less Qubic transfers for streaming payments") [V]; but no demand evidence, and the adjacent x402 machine-payments lane is being built by QPayhub (merchant receipts, POS, oracle price feed) [V/I]. Watch as fallback, do not lead with it.

---

## 6. Detailed Project Specification

### 6.1 Product thesis
The cost of producing one additional Qubic smart-contract developer should drop from "a VPS and a multi-repo setup ritual" to "open a URL." QuIDE removes every local prerequisite (Linux, AVX2, 24–32 GB RAM, 25–50 GB/day disk, Docker) by hosting the official toolchain per user, and removes the hackathon bottleneck (manual SSH-node provisioning) by instantiating isolated devnets programmatically. It is deliberately **not** a new chain, not a token, and not an AI codegen product.

### 6.2 MVP features (3–5)

1. **Browser workspace.** One-click cloud IDE (Monaco or code-server) preloaded with a current `qubic/core` checkout, `qpi.h` context-aware editing, template gallery (EmptyTemplate, Random, HM25-style, token examples), integrated terminal, compile + GTest runner button (uses `contract_testing.h` harness), and `qubic-contract-verify` results inline. [Substrate: V]
2. **One-click isolated devnet.** Ephemeral private testnet (based on official core-lite / AIO compose) per project: funded test identities, faucet, RPC/WS endpoint, ticking; automatic teardown and snapshot/restore; replaces the manual hackathon `deploy.sh`/`cleanup.sh` cycle with "Rebuild & redeploy." [Substrate: V]
3. **Deploy + observe.** Deploy the edited contract into the project devnet in minutes; live qlogging event stream in the UI; CLI console baked in; explorer-lite view for contract state. [Substrate: V]
4. **Share & collaborate.** Team workspaces, invite links, read-only "judge/reviewer" URLs (hackathon validation mode), GitHub integration, and headless CI that runs compile + tests + verification on push. [I: no existing product; demand from hackathon workflow V]
5. **Hackathon/education mode.** Seat bundles with pre-warmed workspaces, credit pools sponsored by Qubic/partners, and a leaderboard-compatible submission view. [V: hackathon scale + LabLab partnership]

### 6.3 Explicit non-goals
- **No AI chatbot or AI code generation** as a core feature (risk of gimmick; explicitly in the brief's rejected-idea family). AI-assisted *hints* can come later via existing partners (qbuild).
- No proprietary contract format or new L1 features; no sidechain; no token.
- No bypass of mainnet governance (PR → proposal → IPO flow remains untouched) [V].
- No mainnet hosting of contract execution; devnets are explicitly test environments, with fidelity limits stated in-product.
- No generic-purpose cloud IDE for other languages (focus = QPI C++ and its exact toolchain).

### 6.4 Positioning vs. adjacent products
- **vs. qforge/qubicdev.com (deploy/interact, faucet):** integrate their faucet/testnet where possible; the IDE/workspace is the missing layer, not a clone. [V]
- **vs. qbuild (audit):** complementary; pipe contracts to qbuild-style auditing as an optional gate (partner, don't compete). [V]
- **vs. Qubihub (in-dev all-in-one):** monitor; our defensible moat is hosted compute + devnet orchestration + CI, not UI surface. If Qubihub ships a workspace, pivot to "devnets/CI backend for it." [V/I]
- **vs. AIO kit (official, free):** AIO kills the *Linux-with-hardware* excuse only on capable Linux machines; we sell convenience, collaboration, and multi-tenant isolation to everyone else, and to events that must provision N environments in an hour. Free tier keeps the moral high ground. [V]

---

## 7. Technical Feasibility

**7.1 Reuse, don't reinvent.** Every hard component is open source and verified:
core-lite (local testnet, 16 GB, no EFI) [V]; AIO dev-kit docker-compose stack (core + faucet + wallet + RPC + explorer), explicitly a one-command blueprint [V]; `contract_testing.h` GTest harness [V]; `qubic-contract-verify` restriction checker [V]; qubic-cli [V]; qlogging [V]; explorer frontends [V].

**7.2 The novel engineering** is orchestration and multi-tenancy:
- Per-workspace containers (the AIO compose stack trimmed per plan tier) with lifecycle management, pre-warming, and autosuspend; snapshot/restore of devnet state; per-tenant RPC routing (each devnet has its own endpoint) [I].
- Sandboxing user compilation/execution (gVisor/Firecracker/nsjail class isolation), CPU/disk quotas; disk-growth control via tick-rate tuning (`TICK_DURATION_MS`-style slowdown documented in AIO: halves write volume) [V].
- Editor: hosted Monaco or VS Code server with QPI syntax pack; compile pipeline wrapping the repo's own build.
- CI: headless worker running the same container image without an editor; GitHub App integration.

**7.3 Unknowns to prototype first (each < 1 week):**
(a) cold-start time of a devnet on cheap VPS classes (target: workspace ready < 90 s, devnet < 120 s);
(b) steady-state cost per idle vs active workspace (target: ≤ $8–12/month idle, ≤ $0.30/active-hour) — decide pooling strategy from measured numbers;
(c) deploy-to-event loop latency (edit → redeploy → event visible) target < 3 min;
(d) fidelity delta between single-node devnet and mainnet tick semantics (document, don't hide).

**7.4 Feasibility verdict:** high. The riskiest part is unit economics and sandboxing, both measurable in a 2-week spike. [I]

---

## 8. Commercial Case

**A. Thesis.** Developer tooling with a free tier and paid collaboration/CI is the standard, proven SaaS shape (GitHub Codespaces, Gitpod, Replit) [I]; Qubic's specific, verified absence of any equivalent, plus a recurring hackathon funnel (1,654 participants, 265 teams in one event) [V], gives a narrow but real wedge. Revenue diversity: individual seats, team seats, event/education bundles, enterprise self-host licenses, CI minutes. **No token.**

**B. Competitive analysis.** Direct competitors: none in-ecosystem (§4). Adjacent: qforge, qbuild, Qubihub, Qubic.NET.Toolkit, official AIO kit — all analyzed; integration path preferred over head-on overlap (§6.4). External analogy (codespaces-style products) proves the category but not Qubic pricing power [I].

**C. Product spec.** Section 6.2 (features + non-goals).

**D. Technical plan + unknowns.** Section 7. Prototype unknowns first (§7.3).

**E. Business model (all pricing [U], to be validated in §11):**
- **Free:** 1 concurrent workspace, 1 short-lived devnet/day, public projects — aligns with Qubic's open-source culture and keeps AIO users on our surface.
- **Pro** ($19–29/dev/month): always-warm workspace, 2 devnets, CI minutes included.
- **Team** ($99–199/month/org): private projects, concurrent devnets, reviewer links, SSO later.
- **Usage:** extra devnet-hours and CI overage (metered).
- **Events/Education:** per-seat packages purchased by Qubic Foundation/partners (this is a sponsorship-shaped B2B2C channel with a verified buyer motive: they currently hand-provision nodes at their own cost).
- **Enterprise:** self-hosted orchestration license for partners (institutions building Qubic integrations [V: Onyze/Vottun-style actors]).

**F. Milestones & acceptance criteria.** Section 9.

**G. Budget.** Section 9.

**H. Risks.** Top 5 with stop conditions — section 10.

**I. Pre-application validation.** Section 11.

---

## 9. Milestones and Budget

Payment-after-delivery model of the Incubation Program [V] means milestones must each be independently testable and fund-able; plan working capital accordingly. Budget figures are planning estimates [I], to be refined after the prototype spike.

> **Budget revision (Oct 2026):** the team caps the program ask at **$30K / ~12 weeks** with trimmed scope. The $115K table below was the research-stage estimate for the full-feature build; the current, authoritative plan is `docs/09-milestones-budget.md` in the proposal repo.

| # | Milestone | Duration | Acceptance test (objective) | Cost |
|---|---|---|---|---|
| M1 | **Workspace MVP**: hosted IDE on official core checkout; compile + GTest run + contract-verify in browser; 2 starter templates | 3 wks | A new user with no local tools compiles `EmptyTemplate` and passes its tests in-browser; cold-start < 120 s (p90) in test cohort | ~$8K |
| M2 | **One-click devnet**: ephemeral isolated testnet per project (faucet, funded identities, RPC); rebuild/redeploy cycle automates hackathon `deploy.sh`/`cleanup.sh`; full-state snapshots | 3 wks | Time from "create project" to "my contract answers a CLI call on my devnet" < 10 min, measured on ≥3 teams | ~$9K |
| M3 | **Observe & share**: qlogging stream in UI, explorer-lite state view, shareable reviewer links, GitHub push → CI (compile+tests+verify) | 3 wks | Any push triggers CI within 60 s; test job < 5 min; a shared link lets a reviewer call a contract function without an account | ~$7K |
| M4 | **Beta in a hosted event cohort**: pre-warmed seats, credits, submission view; ≥10 external teams active | 3 wks | ≥10 teams with ≥1 successful deploy; ≥50% return in week 2; published status page | ~$6K |
| — | Buffer (~8%) embedded in tranche amounts; no separate contingency tranche | — | — | — |
| | **Total to beta (revised)** | **~12 wks** | | **~$30K** |

Team: two founder-engineers at below-market stipends (difference deferred to the revenue-share return), ≈0.15 FTE C++/Qubic consultant, part-time design. Open-source core components retained under their licenses; company's orchestration layer proprietary. [I]

---

## 10. Risk Assessment

| Risk | Likelihood | Impact | Mitigation | **Stop condition** |
|---|---|---|---|---|
| Qubic core/QCT ships its own hosted IDE/devnet (Qubihub evolves, AIO goes cloud) | Medium | High | Position as backend/partner; offer to power their surface; non-compete check is a go-gate (§11) | Core announces an official hosted workspace with a roadmap date — pivot to devnet/CI backend or shelve |
| Willingness-to-pay never materializes (devs are few, used to free tools) | Medium-High | High | Validate before building (interviews, LOIs, concierge); B2B2C event sponsorship as revenue floor; freemium funnel | <3 paid pilot commitments after validation — fall back to candidate #2/#15 or NO-GO |
| Unit economics (devnets are heavy: RAM/disk/tick writes) | Medium | Medium | Pooling, autosuspend, tick-rate tuning (documented halving of disk writes [V]), quotas; measure in spike | Steady-state cost per active dev-hour > 2× price of cheapest tier — re-architect or abandon |
| Multi-tenant compilation/security incident (abuse of build sandbox) | Low-Medium | High | Hard sandboxing (gVisor/Firecracker-class), egress limits, per-tenant quotas, no secrets in build env | Any confirmed sandbox escape class — halt beta, external review |
| Ecosystem dev flow stalls (few new contract teams; hackathon dependency) | Medium | Medium | Diversify channels: grants-program recipients, Nostromo-track teams, enterprise integrations; keep costs variable | <5 active paying teams at month 12 — downsize to maintenance mode |
| Protocol/toolchain drift breaks the hosted stack (frequent core releases, tick-rate changes) | Medium | Low-Medium | Pin core versions per workspace; automated regression image builds; "upgrade devnet" button | Two consecutive core releases break workspace creation > 48 h — pause paid plans |

---

## 11. Validation Plan (pre-application, ≤ 3 weeks, ≤ $2K)

1. **Interviews (n ≥ 10)** — hackathon participants (Madrid/Paris/Hack-the-Future registrations), Nostromo-track teams, grant recipients, active `#dev` members; script: last contract attempt, where you got stuck, what you paid (VPS spend is a measurable proxy), would you pay $X for hosted devnets. Record verbatim. [V: participant pools exist]
2. **Concierge MVP (the decisive test)** — use the official AIO kit automation to provision isolated devnets for 3–5 real teams manually; measure time-to-first-deploy and weekly active usage for 3 weeks. This directly mimics the MVP's core value with ~zero code. [V: AIO substrate]
3. **Pricing probe** — landing page with three price anchors + waitlist; track conversion to "notify me + would pay" clicks; target ≥25 qualified signups or ≥3 LOIs.
4. **Non-compete confirmation** — ask QCT/incubation team directly in Discord #dev or via the incubation contact: "Is a hosted IDE/devnet planned? We intend to answer the Open Code Editor RFP as a commercial product." [V: RFP is public]
5. **Cost spike** — 1 devnet on a Hetzner-class VPS + 1 workspace; measure cold start, RAM/disk/day at default and slowed tick rates, monthly run-rate per tier. [I: benchmarks to be produced]

**Decision rule:** all three go-gates (§1) verified → write application; any gate fails → fallback per §1.

---

## 12. Incubation Fit

**Process fit [V]:** the current Incubation Program page describes an Incubation Board review of **1–2 weeks** on impact/feasibility/alignment, milestone-based development with QA, **payment only upon delivery (no upfront — plan working capital)**, one covered smart-contract audit if needed, mainnet support, and an AMA. Note the discrepancy with the older (Oct 2024) announcement describing initial funding and a ≥55% Discord community vote [V: blog] — the report flags this; the application should reference the current page as authoritative and ask the board to confirm the funding mechanics.

**Mission fit:** dev tooling is explicitly on Qubic's wanted list ("Developer tools", "SC Builder for dummy's", plus the standing Online Code Editor RFP) [V]; the product's KPI (external contract teams per quarter) is the ecosystem's own growth KPI; no token, no regulatory exposure; open-source-friendly; the app itself can be delivered in 4 testable milestones matching the payment-on-delivery model.

**Why this beats the alternatives inside the program's economics:** it needs no smart-contract IPO (no 676-share all-sell risk [V]), no oracle dependencies, no liquidity bootstrapping — the entire risk is product-market fit, which is cheap to test (§11).

---

## 13. Draft Application Description

*(Ready to adapt for the incubation application form / proposal repo README.)*

> **Project name:** QuIDE — Browser-Based Workspaces and One-Click Devnets for Qubic Smart Contracts
>
> **One-liner:** QuIDE gives Qubic developers browser-based workspaces and one-click private devnets for C++ smart contracts — zero local setup, from idea to a running contract on your own isolated testnet in under ten minutes.
>
> **Problem:** Building a Qubic smart contract today requires a Linux x86-64 machine with AVX2, 24–32 GB RAM and 25–50 GB/day of disk write capacity just for the official local environment, and teams or hackathon participants must request hand-provisioned test nodes from organizers. macOS and Windows laptops cannot run the sanctioned one-command setup at all. This is the ecosystem's largest developer-onboarding bottleneck, and Qubic's own grants repository still lists an unfilled RFP for an online C++ contract editor.
>
> **Solution:** A hosted development platform that packages the official open-source toolchain (core-lite, AIO dev-kit stack, GoogleTest harness, contract-verify, CLI, qlogging) into per-user cloud workspaces with one-click isolated devnets, integrated compilation/testing/verification, shareable review environments, and CI. Hackathon and education modes let Qubic and partners pre-warm hundreds of environments and fund seats with credits.
>
> **Why now:** Qubic just consolidated its local tooling (AIO dev kit, July 2026) into a containerized stack that is trivially hostable; hackathons are recurring and large (1,654 participants and 265 teams in December 2025 alone); and no hosted product exists. Execution risk is low because every subsystem already exists — our work is orchestration, multi-tenancy and experience.
>
> **Business model:** freemium SaaS (free tier → $19–29/dev/month Pro → team plans → metered devnet/CI usage), event/education bundles purchased by ecosystem partners, and self-hosted enterprise licenses. No token.
>
> **Milestones:** (1) hosted workspace with in-browser compile/test/verify; (2) one-click devnets + deploy cycle; (3) observability, sharing and CI; (4) beta with ≥10 external teams in a hosted event cohort. Each milestone has a public acceptance test (time-to-first-deploy, cold-start time, CI duration, active-team counts).
>
> **Team & budget:** two founder-engineers + ≈0.15 FTE C++ consultant; ~$30K over ~12 weeks including infrastructure (below-market founder stipends, difference deferred); potential follow-on: template/library work aligned with the OpenZeppelin-equivalent RFP, and devnet/CI backend partnerships with qforge, qbuild and Qubihub.

---

## 14. Proposal Repository Outline

Suggested repository `quide-proposal` (public or shared with the board):

```
README.md                  — summary, verdict, links to evidence index, milestone table
/research
  this-report.md           — full research report (this document)
  evidence-index.md        — every URL cited, with [V]/[I]/[U] tags and date accessed
  interviews/              — validation interview notes (n≥10) and consent/verbatim
  pricing-probe/           — landing page copy, waitlist numbers, LOI scans
/architecture
  overview.md              — container topology, devnet lifecycle, CI path (diagrams)
  sandboxing.md            — isolation model, quotas, egress policy
  fidelity.md              — devnet vs. mainnet semantics and documented limitations
/cost-model
  unit-economics.xlsx/csv  — measured (not assumed) cost per idle/active workspace and devnet
  assumptions.md           — VPS classes, tick-rate tuning, pooling strategy
/milestones
  M1-workspace.md .. M4-beta.md — deliverable, acceptance test, demo script, cost
/validation
  go-gates.md              — the 3 gates, status, evidence
/prototype
  concierge-runbook.md     — exact steps used for the manual devnet pilot (repeatable)
  scripts/                 — AIO-kit automation glue used in the pilot
/legal
  licenses.md              — open-source inventory + license compliance
  privacy.md               — seed/key handling policy (no seeds ever stored server-side)
/team
  CVs / capabilities + C++/Qubic advisor agreement summary
```

---

## Appendix A — Source Index

**[V] Verified sources (accessed Oct 2026):**
- Incubation program: https://qubic.org/incubation-program · announcement: https://qubic.org/blog-detail/introducing-the-qubic-incubation-program
- Grants program + RFPs (Online Code Editor; OpenZeppelin-equivalent; Gnosis-like multisig): https://github.com/qubic/grants · application: https://tally.so/r/n9l50Q
- Dev environment requirements: https://docs.qubic.org/developers/dev-kit · https://docs.qubic.org/developers/smart-contracts/getting-started/setup-environment
- Testnet resources (dedicated nodes, isolation, best practices): https://docs.qubic.org/developers/testnet-resources
- Contract lifecycle (verification tool, PR, proposal, IPO, reserve): https://docs.qubic.org/developers/smart-contracts/lifecycle
- Contract testing (GTest harness): https://docs.qubic.org/developers/smart-contracts/testing/contract-testing
- AIO kit: https://github.com/qubic/aio-qubic-dev-kit (created 2026-07-22; replaces archived qubic-dev-kit) · core-lite: https://github.com/qubic/core-lite
- Hackathon hub (manual node provisioning, deploy/cleanup cycle, faucet, RPC): https://github.com/qubic/qubic-hackathon
- Hackathon scale & LabsLab partnership: https://lablab.ai/ai-articles/qubic-ai-hackathon-case-study · Madrid recap: https://qubic.org/blog-detail/qubic-vottun-2025-madrid-hackathon-recap · Hack the Future: https://qubic.org/blog-detail/qubic-hack-the-future-hackathon
- Ecosystem directory (~47 entries): https://qubic.org/ecosystem (+ per-project pages: qforge, qbuild, Qubihub, Easy Connect, Qubic Metrics, QSwap, Qubic Core Lite, etc.)
- Core contracts fleet (incl. QIP, QPayhub, QReservePool, VottunBridge, MsVault): https://github.com/qubic/core/tree/develop/src/contracts
- Core-bob indexer: https://github.com/qubic/core-bob · Qubic.NET.Toolkit: https://github.com/qubic/Qubic.NET.Toolkit
- Prior-art attempts: https://github.com/HildaPosada/Qubic-hackathon- (Nov 2025) · https://lablab.ai/ai-hackathons/raise-your-hack/ghost-qubic-track/qubilearn (Jul 2025)

**[I] Inferred (analysis from verified sources):** unit-economics ranges, competitive positioning, SaaS category comparisons, CI absence, MVP architecture choices.

**[U] Unvalidated (hypotheses to be tested in §11):** willingness-to-pay and pricing anchors, conversion targets, runner-up lane assessments (payments/lending), point-in-time market-depth figures.

---

*End of report. Next action if GO conditions are pursued: execute §11 (validation), then convert §13 into the live application and §14 into the proposal repository.*
