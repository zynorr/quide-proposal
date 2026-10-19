# Why Now, Why Qubic

## Why now
1. **The substrate just appeared.** The official AIO Qubic Dev Kit (created 2026-07-22; supersedes the archived Madrid-2025 kit) packages core + faucet + wallet + RPC + explorer into one `docker compose` stack, and core-lite provides a 16 GB local testnet without EFI. Hosting a first-class cloud workspace is now an engineering-composition problem, not a research problem. **[V]** - [github.com/qubic/aio-qubic-dev-kit](https://github.com/qubic/aio-qubic-dev-kit), [docs.qubic.org/developers/dev-kit](https://docs.qubic.org/developers/dev-kit)
2. **The gap is officially acknowledged and still open.** The grants repo's "Online Code Editor for C++ Smart Contracts" RFP is unclaimed, and the ecosystem directory contains no hosted IDE or devnet product after multiple hackathons and ten incubated projects in other lanes. **[V]** - [github.com/qubic/grants](https://github.com/qubic/grants)
3. **The demand keeps recurring at scale.** Madrid 2025 (127 hackers), Raise Your Hack Paris, and Hack the Future (1,654 participants / 265 teams, Dec 2025) - every event solved environment access manually. **[V]** - [Qubic blog](https://qubic.org/blog-detail/qubic-vottun-2025-madrid-hackathon-recap), [lablab.ai](https://lablab.ai/ai-articles/qubic-ai-hackathon-case-study)
4. **The rest of the stack is done.** Wallets (including Ledger, live July 2026), bridges (Ethereum live, Solana in QA), DEXs, indexers, and analytics are shipped or in flight; the remaining visible bottleneck is producing new external contracts. **[V]**
5. **The incubation path exists.** The Qubic Incubation Program is active with a defined review process and milestone-based funding; this proposal is built for that process and its payment-on-delivery model. **[V]** - [qubic.org/incubation-program](https://qubic.org/incubation-program)

## Why this product is Qubic-shaped
- **Feeless, fixed-fee transactions:** iterating a contract in a dev loop is cheap and fast by design - no gas auctions between idea and test. **[V]**
- **QPI's restricted bare-metal C++** (no pointers, floats or arrays; no `#include`; no local variables) makes verification and testing tooling *mandatory*, not optional - QuIDE bakes `qubic-contract-verify` and the GoogleTest harness into the workflow as first-class steps. **[V]** - [developer guidelines](https://github.com/qubic/core/tree/develop/src/contracts)
- **The contract lifecycle gates on testing:** PR → proposal → IPO (all 676 shares must sell) → go-live; a pre-flight environment de-risks every stage before governance is involved. **[V]** - [lifecycle docs](https://docs.qubic.org/developers/smart-contracts/lifecycle)
- **Every external contract compounds:** new contracts add dividends and utility; external developer throughput is the network's binding constraint. **[I]**

## Why this cannot be a generic cloud IDE
The value is Qubic-specific orchestration: core-lite / dev-kit topology, QPI restrictions and verification, the GoogleTest contract harness, epoch/tick semantics, and hackathon seat provisioning. A generic IDE adds nothing here; this removes the exact barriers documented in [02-problem-icp.md](02-problem-icp.md). **[I]**
