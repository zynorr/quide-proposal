# Product & Demo

## Main user flow (target: < 10 minutes from signup to running contract)
1. **Sign up** (GitHub or email) → "New project" → choose a template (EmptyTemplate, Random, token example, HM25-style).
2. **Workspace opens** — current `qubic/core` checkout, Monaco / VS Code editor, terminal, preloaded QPI context.
3. **Edit** the contract; **Run checks** — one click runs compile, the GoogleTest harness, and `qubic-contract-verify`; results shown inline.
4. **Create devnet** — one click provisions an isolated private testnet for this project: faucet, funded test identities, RPC/WS endpoint; state snapshots on demand.
5. **Deploy** — "Rebuild & deploy" replaces the manual `deploy.sh` / `cleanup.sh` cycle; contract live on your devnet in minutes.
6. **Interact & observe** — CLI console to call functions/procedures; live qlogging event stream; explorer-lite state view.
7. **Share** — invite teammates or generate a read-only reviewer link (e.g., for hackathon judges).
8. **CI** — connect GitHub; every push runs compile + tests + verification headlessly.

## MVP scope
**In:** the five MVP features (browser workspace, one-click devnet, deploy + observe, share + CI, event mode); free tier (1 workspace, short-lived devnets); Pro/Team tiers; event seat bundles; GitHub integration.

**Explicit non-goals:** no AI chatbot or code-generation core; no proprietary contract format; no new L1 features or sidechain; no mainnet governance bypass (PR → proposal → IPO unaffected); no generic multi-language cloud IDE; no token.

## Demo
- **Today (pre-build): the concierge pilot.** We manually provision an isolated devnet for a design partner using the official AIO dev-kit automation and walk the flow above with them. Reproducible steps: [demo/README.md](../demo/README.md).
- **At MVP (M1–M2):** recorded walkthrough + screenshots in [demo/](../demo/); placeholders are listed there.
- **Board demo narrative:** from signup (no local tools) to a contract answering a CLI call on a private testnet, timed end-to-end — target < 10 minutes.

## Architecture (sketch)
- One containerized **workspace** per developer: editor + toolchain image built on the official AIO stack, trimmed per tier. **[I]**
- One **ephemeral devnet** per project (core-lite-based), lifecycle-managed: create → seed → snapshot → suspend → resume → destroy; per-tenant RPC/WS endpoint. **[I]**
- **CI:** the same image, headless (compile + GoogleTest + contract-verify), triggered by GitHub push. **[I]**
- Deployment on commodity VPS/Kubernetes; aggressive autosuspend and tick-rate tuning to control disk/CPU cost. **[I]**

## Key technical risks (to prototype in the first two weeks)
| Risk | Why it is risky | First test |
|---|---|---|
| Multi-tenant isolation | Untrusted C++ compilation/execution | Sandbox escape review (gVisor / Firecracker class) |
| Unit economics | Devnets are RAM/disk heavy | Measure idle/active cost per workspace and devnet on commodity VPS |
| Cold-start times | The UX promise is "minutes" | Measure workspace < 120 s, devnet < 120 s |
| Devnet fidelity | Single-node devnet vs. 676-computor mainnet | Document semantic gaps in-product; regression against the official harness |
