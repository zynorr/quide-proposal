# Milestones & Budget

All figures in USD; planning estimates **[I]**. Milestones are shaped for tranche-based, payment-on-delivery funding.

> **Ask: $30K over ~12 weeks, in four tranches.** Revised Oct 2026 from the research-stage $115K estimate ([../data/QUBIC-INCUBATION-RESEARCH-REPORT.md](../data/QUBIC-INCUBATION-RESEARCH-REPORT.md) §9, flagged as superseded there); scope trimmed accordingly — no separate contingency tranche, ~8% buffer embedded.

## Budget by tranche
| # | Milestone (deliverable) | Duration | Cost | Use of funds |
|---|---|---|---|---|
| M1 | **Hosted workspace** — browser IDE on the official core checkout; compile + GoogleTest + `qubic-contract-verify`; 2 starter templates | 3 wks | **$8K** | Founder stipends, infra |
| M2 | **One-click devnets** — isolated private testnet per project (faucet, funded identities, RPC/WS), full-state snapshots, rebuild/redeploy automation | 3 wks | **$9K** | Founder stipends, C++ consultant, infra |
| M3 | **Observe, share, CI** — qlogging stream, state view, reviewer links, GitHub push pipeline | 3 wks | **$7K** | Founder stipends, design, infra, targeted security review |
| M4 | **Event beta** — one hosted cohort (pre-warmed seats, credits) with ≥10 external teams | 3 wks | **$6K** | Founder stipends, event support, infra |
| | **Total** | **~12 wks** | **$30K** | ~8% buffer embedded; no separate contingency tranche |

Rough split: founder stipends ~53% (two engineers, below market; the difference is deferred against the revenue-share return — [08-return-to-incubation.md](08-return-to-incubation.md)), C++/Qubic consultant ~20% (≈0.15 FTE), infrastructure ~8%, design ~5%, event support ~5%, embedded buffer ~8%.

## Acceptance criteria (objective, testable from the user's perspective)
| # | Acceptance test | Method |
|---|---|---|
| M1 | A user with no local tools signs up, opens a workspace, compiles a template, passes its tests, and sees verification results; cold start < 120 s (p90) | Screen-recorded runs on 3 unprovisioned machines; logs |
| M2 | From "New project" to a contract answering a CLI call on its own devnet in < 10 minutes, including faucet funding; rebuild/redeploy automates cleanup | Timed runs with ≥3 external teams |
| M3 | GitHub push triggers CI < 60 s; compile + tests + verify job < 5 min; reviewer link allows a no-account function call | Public demo with a partner team |
| M4 | ≥10 external teams deploy ≥1 contract in the hosted cohort; ≥50% return in week 2; post-event survey ≥ 4/5 usefulness | Event data + survey |

## Dependencies & assumptions
- Official stack remains available and open source: core-lite, AIO dev-kit, GoogleTest harness, contract-verify, qubic-cli, qlogging. **[V]**
- Commodity cloud pricing stays within E5 measurements; the AVX2 baseline is available on standard x86 VPS classes. **[I]**
- A partner event or hosted cohort can be scheduled for M4 (~week 10–12), following the LabLab / Qubic hackathon cadence. **[V/I]**

## Payment-on-delivery note
Each tranche is released on milestone acceptance per the current program page; the team carries M1–M2 stipends and infrastructure from its own runway. If the board's mechanics differ (older announcement), the tranche mapping is adapted. **[V]**
