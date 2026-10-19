# Business Model & Pricing

**All prices below are hypotheses [U], currently being tested in E1/E3 - see [05-validation-traction.md](05-validation-traction.md).**

## Revenue lines
| Line | What | Price (hypothesis) | Why it fits delivered value |
|---|---|---|---|
| **Free** | 1 workspace, 1 short-lived devnet/day, public projects | $0 | Keeps AIO users on our surface; top of funnel; fits ecosystem open-source culture |
| **Pro** | Always-warm workspace, 2 concurrent devnets, CI minutes | $19-29 / dev / month | Replaces a $40-100+/mo VPS plus hours of ops; a seat is the developer's daily environment |
| **Team** | Private projects, more devnets, reviewer links, shared templates, priority support | $99-199 / org / month | Team value is collaboration and isolation; buyer is the team lead |
| **Usage** | Extra devnet-hours, CI overage | Metered | Aligns cost-to-serve (compute) with price - margin protection |
| **Events / Education** | Seat bundles, pre-warmed environments, sponsor-funded credits | Per-event package | Organizers already absorb this cost with manual ops **[V]**; the budget line exists |
| **Enterprise** | Self-hosted orchestration license or dedicated support | Annual license | Partner integration teams need reproducibility and compliance |

## Why the pricing metric fits
The metered units - **workspace-months + devnet-hours** - track exactly what we pay for (RAM/CPU/disk) and what the user receives (an always-available environment plus isolated compute). The free tier is constrained by time (short-lived devnets) rather than features, so it teaches the product without draining margins. **[I]**

## Unit-economics targets (to verify in E5)
- Idle workspace: **≤ $8-12/month** → Pro at $19-29 retains > 60% gross margin. **[U]**
- Active devnet-hour: **≤ $0.30** → usage tier priced ≥ $0.60/h. **[U]**
- If either target is missed by more than 2×, re-architect (pooling, tick-rate tuning, spot instances) before scaling. **[I]**

## Why no token
Revenue is subscription and usage based; Qubic transactions are feeless/fixed-fee, so there is no gas arbitrage to monetize. A token would add regulatory and trust overhead with zero product benefit, and the ecosystem's public-goods programs signal a preference for non-token infrastructure. **[I]**

## Evidence-driven pricing process
1. **E1 interviews** - capture current spend (VPS bills, ops hours) and stated willingness to pay.
2. **E3 landing page** - three anchors ($9 / $19 / $29) plus waitlist; measure qualified interest.
3. **E2 pilot** - offer paid conversion at the end of week three to at least three teams; collect letters of intent at the chosen price.
