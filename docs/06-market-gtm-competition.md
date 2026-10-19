# Market, GTM & Competition

## Bottom-up market logic
The market is "Qubic smart-contract development capacity." Sized bottom-up, not top-down:

- **Hackathon funnel:** one online event = ~1,600 participants, 265 teams **[V]**. Events recur multiple times per year (Madrid, Paris, Hack the Future) **[V]**. Every participant needs an environment; every team needs an isolated devnet.
- **Contract teams:** external teams building on Qubic today number in the dozens, not thousands **[U]** — Nostromo-track teams, grant recipients, community contracts. This is the core paying base: ~2–5 seats each.
- **Onboarding / education:** Qubic Academy and docs audience; converting to a first contract is the free tier's job.
- **Partners / enterprises:** integration teams needing reproducible, compliant builds (self-host tier).

**Sketch (all [U], to be tested):** 300 active external Qubic developers × $20/mo × 10% paid conversion ≈ **$600 MRR (≈ $7.2K ARR)** steady-state; plus 3 events/yr × ~1,500 seats × ~$1/seat/day × 3 days ≈ **$13.5K/yr** sponsor-funded; plus enterprise licenses. Conclusion: viable as a lean, variable-cost SaaS **only if Qubic's developer inflow grows**. Our costs scale with usage, not headcount.

## Buyer vs user
- **User:** the developer.
- **Buyer:** team lead / CTO (Team plan); hackathon organizer or ecosystem fund (seat bundles); enterprise integration lead (self-host).
- **Sponsor motivation (verified):** organizers already absorb this cost through manual ops and infrastructure. **[V]** — [hackathon repo](https://github.com/qubic/qubic-hackathon)

## Alternatives today and why they fall short
| Alternative | Cost | Why insufficient |
|---|---|---|
| Official AIO kit, self-hosted | Free + Linux machine or VPS ($40–100+/mo) + hours of setup | Excludes macOS/Windows laptops; 24–32 GB RAM; 25–50 GB/day disk; single-player; no CI **[V]** |
| Organizer-provisioned SSH nodes | "Free" | Manual, scarce, no collaboration, no CI, tied to events **[V]** |
| Local Visual Studio + core unit tests | Free | Unit tests only; no running devnet without core-lite + hardware; no team isolation **[V]** |
| Generic cloud IDEs (Codespaces etc.) | $0–40+/mo | No Qubic toolchain (QPI, harness, verify, devnet ops); customer must assemble it **[I]** |
| Hackathon IDE projects | Free | Unmaintained one-off demos (Nov 2025, Jul 2025); no devnets, CI, or ops **[V]** |

## In-ecosystem adjacency and positioning
| Product | What it does | Relationship |
|---|---|---|
| qforge (Latio) | Deploy/interact UI + testnet + faucet | Adjacent — integration partner (faucet/testnet), not competitor **[V]** |
| qbuild (Kairos) | AI audit/test of contracts | Complementary — optional audit gate; partner **[V]** |
| Qubihub | In-dev explorer + utilities "all-in-one" | Closest timing risk — monitor; offer devnet/CI backend if it ships a workspace **[V/I]** |
| Qubic.NET.Toolkit | Desktop interaction / DeFi client | Complementary (post-deploy interaction) **[V]** |

## Acquisition channels (ranked)
1. **Hackathons** — presence and seat bundles; the recurring moment of maximum need (LabLab partnership exists **[V]**).
2. **Discord `#dev`** — support-led growth; templates shared as working examples.
3. **Ecosystem directory + docs listing** — discovery once live.
4. **Grants / Nostromo onboarding** — every funded team gets a workspace; the programs become the channel.
5. **Content / education** — tutorials built on QuIDE sessions ("deploy your first contract in 10 minutes").

## Moat
Orchestration and operational know-how (multi-tenant devnet lifecycle, cost control), deep Qubic toolchain integration, a community-co-developed template library, and team-level switching costs (projects, CI, shared review links). Not a UI moat — a reliability and cost moat. **[I]**
