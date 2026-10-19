# QuIDE — One-Page Summary

**One-liner:** Browser-based workspaces and one-click private devnets for Qubic C++ smart contracts — from idea to a running contract on your own isolated testnet in under ten minutes, with zero local setup.

## Problem
Qubic's sanctioned local development environment is out of reach for most developers: Linux x86-64 + AVX2 only, ≥24 GB RAM (≥32 GB with explorer), 8+ cores, 25–50 GB/day disk writes — official docs call it *"a real dev environment, not a laptop toy"* and tell non-Linux users to rent a VPS. Team and hackathon isolation requires hand-provisioned dedicated test nodes requested from organizers, and there is no hosted CI. Qubic's own grants repository still lists an unclaimed RFP for an online C++ smart-contract editor. **[V]**

## User
External smart-contract developers: hackathon participants (~1,600 people / 265 teams in the December 2025 online event), Nostromo-track and grant-funded contract teams, onboarding developers and educators, and integration partners prototyping on Qubic. **[V]**

## Why Qubic
The missing layer is the develop → compile → test → simulate loop, and Qubic is an ecosystem where it can be hosted cheaply: feeless fixed-fee transactions, bare-metal contracts, and an official open-source stack (core-lite, AIO dev-kit, GoogleTest harness, contract-verify, CLI, qlogging) already packaged as a docker-compose stack. Every new external contract adds to the network's dividends and utility; developer throughput is the ecosystem's binding constraint. **[V/I]**

## Ask
**$30K over ~12 weeks, in four delivery tranches** (~8% buffer embedded; no separate contingency), matching the program's milestone / payment-on-delivery model. Covers two founder-engineers at below-market stipends (the difference is deferred against the revenue-share return), a ≈0.15 FTE C++/Qubic consultant, part-time design, and infrastructure. **[I]**

## Milestones
| # | Milestone | Acceptance test |
|---|---|---|
| M1 | Hosted workspace: in-browser compile + GoogleTest + contract-verify | New user compiles `EmptyTemplate` and passes tests in-browser; cold start < 120 s (p90) |
| M2 | One-click isolated devnet + rebuild/redeploy cycle | Create project → contract answers CLI call in < 10 min, verified on ≥3 external teams |
| M3 | Observe, share, CI: event stream, reviewer links, push-triggered pipeline | Push → CI starts < 60 s; test job < 5 min; reviewer link works without account |
| M4 | Hosted event cohort with ≥10 external teams | ≥10 teams with ≥1 successful deploy; ≥50% return in week 2 |

## Return proposal
Revenue share: **5% of gross revenue**, triggered at first paying customer, **capped at 2.5× disbursed**, quarterly reporting. Negotiable; equity alternative available. Details in [08-return-to-incubation.md](08-return-to-incubation.md).

## Status
Pre-build. Evidence base and 15-candidate elimination audit in [../data/QUBIC-INCUBATION-RESEARCH-REPORT.md](../data/QUBIC-INCUBATION-RESEARCH-REPORT.md); validation gates and current progress in [05-validation-traction.md](05-validation-traction.md).
