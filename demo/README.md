# Demo & Walkthrough

> **Current stage: pre-build.** This folder will hold screenshots, walkthroughs, and reproducible evidence. Right now it contains the **concierge pilot** used in validation (E2).

## Concierge pilot (reproducible, today)
Goal: reproduce QuIDE's core experience manually so design partners can evaluate it before the product exists.

1. Provision a commodity Linux VPS meeting the official AIO requirements (x86-64 with AVX2, ≥24-32 GB RAM, 8+ cores, generous disk). **[V - [docs.qubic.org/developers/dev-kit](https://docs.qubic.org/developers/dev-kit)]**
2. Deploy the official AIO Qubic Dev Kit stack (core + faucet + wallet + RPC + explorer) for the team.
3. Create a project workspace: the team's contract inside a `qubic/core` checkout plus a test file for the GoogleTest harness.
4. Walk the team through the full loop: edit → compile → run tests → run `qubic-contract-verify` → rebuild & deploy on their devnet → call the contract via qubic-cli → watch qlogging events.
5. Instrument timing: time-to-first-deploy, number of deploys during the pilot, week-3 activity.
6. Record results under [../data/pilot-metrics/](../data/pilot-metrics/) and summarize in [../docs/05-validation-traction.md](../docs/05-validation-traction.md).

## Planned artifacts (placeholders until MVP)
- [ ] `screenshots/01-workspace.png` - editor with QPI context and starter templates
- [ ] `screenshots/02-tests.png` - inline GoogleTest + verification results
- [ ] `screenshots/03-devnet.png` - devnet created, RPC endpoint, funded identities
- [ ] `screenshots/04-events.png` - live qlogging stream after a contract call
- [ ] `walkthrough.md` - end-to-end demo script with timings (target < 10 minutes)
- [ ] `video.md` - link to the recorded walkthrough (M2)
