# Problem & Ideal Customer Profile

## The problem in one paragraph
Producing a running, tested Qubic smart contract requires a development environment that most developers cannot run. The official path demands a Linux x86-64 machine with AVX2, ≥24 GB RAM (≥32 GB for the full stack), 8+ cores and ~25-50 GB/day of write capacity; official docs describe it as *"a real dev environment, not a laptop toy"* and direct non-Linux users to rent a VPS. Team isolation - an unavoidable need, since one bad contract change can break a shared testnet - requires asking organizers for a hand-provisioned dedicated SSH node. There is no hosted CI. Qubic's own grants repository carries an unfilled RFP for exactly the missing layer: an online C++ contract editor. **[V]**

## Who has the pain (ICP)

| Segment | Pain | Today's workaround | Why it is insufficient |
|---|---|---|---|
| **A. Hackathon participants** (~1,600 people / 265 teams in one event **[V]**) | Cannot run the official environment on laptops; 48-72 h event clock | Organizer SSH nodes provisioned by hand; VS Code Remote-SSH; manual `deploy.sh` / `cleanup.sh` after every change **[V]** | Does not scale to hundreds of teams; no collaboration or CI; organizers become an ops team; macOS excluded |
| **B. Independent contract teams** (Nostromo track, grant recipients, community contracts) | Need isolated testnets and CI for a team | Personal Linux workstation or rented VPS ($40-100+/mo); GitHub used only as code host **[I]** | High fixed cost for pre-revenue teams; no turnkey testnet/CI; environment drift across machines |
| **C. Onboarding developers / educators** | Learning QPI requires the full stack before "hello world" | Local build; read-only examples; hackathon template | Activation cliff - most never reach a first deploy |
| **D. Partners / enterprises prototyping** | Reproducibility and compliance for builds | Internal infra team builds custom environments | Duplicated effort; no Qubic-specific tooling (contract-verify, test harness) |

## Jobs to be done
1. *"When I join a hackathon, I want a working contract environment in minutes so I spend the event building, not installing."*
2. *"When my team iterates on a contract, we want isolated test environments and automated checks on every push."*
3. *"When I am learning Qubic, I want to see a contract run before I invest in setting up infrastructure."*

## Evidence (primary sources)
- Environment requirements and non-Linux guidance: [docs.qubic.org/developers/dev-kit](https://docs.qubic.org/developers/dev-kit), [setup-environment](https://docs.qubic.org/developers/smart-contracts/getting-started/setup-environment) **[V]**
- Dedicated nodes only "may be provided"; isolation rationale; cleanup-after-testing: [docs.qubic.org/developers/testnet-resources](https://docs.qubic.org/developers/testnet-resources) **[V]**
- Manual per-team node provisioning and deploy/cleanup ritual: [github.com/qubic/qubic-hackathon](https://github.com/qubic/qubic-hackathon) **[V]**
- Unclaimed RFP: [github.com/qubic/grants](https://github.com/qubic/grants) - `RFPs/Online Code Editor for C++ Smart Contracts.md` **[V]**
- Hackathon scale: [lablab.ai case study](https://lablab.ai/ai-articles/qubic-ai-hackathon-case-study) (1,654 participants / 265 teams); [Qubic blog recaps](https://qubic.org/blog-detail/qubic-hack-the-future-hackathon) **[V]**
- No production competitor: ecosystem directory audit (~47 entries, Oct 2026) **[V]**
- Full candidate elimination audit: [../data/QUBIC-INCUBATION-RESEARCH-REPORT.md](../data/QUBIC-INCUBATION-RESEARCH-REPORT.md)
