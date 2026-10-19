# Validation & Traction

**Stage: pre-build, pre-revenue.** No users, pilots, or revenue exist yet. This document records the *evidence base*, the *validation plan*, and the *gates* that decide whether this proposal proceeds to build. Nothing below is presented as traction.

## Verified evidence today (secondary, primary sources linked)
- Official environment barriers and non-Linux guidance - [docs.qubic.org/developers/dev-kit](https://docs.qubic.org/developers/dev-kit), [setup-environment](https://docs.qubic.org/developers/smart-contracts/getting-started/setup-environment) **[V]**
- Manual per-team test-node provisioning and deploy/cleanup ritual - [github.com/qubic/qubic-hackathon](https://github.com/qubic/qubic-hackathon) **[V]**
- Unclaimed "Online Code Editor for C++ Smart Contracts" RFP - [github.com/qubic/grants](https://github.com/qubic/grants) **[V]**
- Recurring, growing hackathon funnel: 127 hackers (Madrid 2025) → 1,654 participants / 265 teams (Dec 2025) - [Qubic blog](https://qubic.org/blog-detail/qubic-vottun-2025-madrid-hackathon-recap), [lablab.ai](https://lablab.ai/ai-articles/qubic-ai-hackathon-case-study) **[V]**
- No hosted IDE/devnet in the ecosystem directory (~47 entries); prior-art attempts are unmaintained - [qubic.org/ecosystem](https://qubic.org/ecosystem) **[V]**
- Full audit and 15-candidate elimination: [../data/QUBIC-INCUBATION-RESEARCH-REPORT.md](../data/QUBIC-INCUBATION-RESEARCH-REPORT.md)

## Validation plan (≤ 3 weeks, ≤ $2K) - status tracker
| # | Experiment | Method | Success threshold | Status |
|---|---|---|---|---|
| E1 | Interviews | ≥10 structured interviews (hackathon alumni, Nostromo-track teams, `#dev` members, grant recipients): last contract attempt, where they got stuck, current VPS spend, willingness to pay | ≥6 confirm the environment friction; ≥3 quote a price they would pay | ☐ planned |
| E2 | Concierge pilot (decisive) | Manually provision isolated devnets for 3-5 real teams using official AIO automation; run 3 weeks | Median time-to-first-deploy < 30 min; ≥50% week-3 retention | ☐ planned |
| E3 | Pricing probe | Landing page with three price anchors + waitlist | ≥25 qualified signups; ≥3 letters of intent | ☐ planned |
| E4 | Non-compete check | Ask QCT / incubation team (`#dev` or direct): is a hosted IDE/devnet planned? Is there positive interest in the RFP being executed commercially? | Explicit confirmation that no near-term hosted product is planned | ☐ planned |
| E5 | Cost spike | One workspace + one devnet on commodity VPS; default vs. slowed tick rates | Idle ≤ $12/mo; active ≤ $0.30/h | ☐ planned |

## Where results will be recorded
Interview notes (consent + verbatim) and pilot measurements are published under [../data/](../data/) (`interviews/`, `pilot-metrics/`, `pricing-probe/`) as they are collected, and summarized here once E1-E3 report.

## Decision rule
All three go-gates must pass before the build application is submitted: **E1** (≥3 letters of intent), **E4** (non-compete confirmation), **E2** (pilot thresholds). If a gate fails, fallback options are documented in [../data/QUBIC-INCUBATION-RESEARCH-REPORT.md](../data/QUBIC-INCUBATION-RESEARCH-REPORT.md) §1.
