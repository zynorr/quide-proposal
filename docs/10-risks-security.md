# Risks & Security

## Security assumptions (product)
- **No secrets in our systems:** customer keys and seeds are never uploaded or stored; contract signing uses external wallets/tools. Devnet identities are throwaway test keys, clearly labeled, with no mainnet value. **[I - design commitment]**
- **Tenant isolation:** untrusted C++ compilation and execution run in sandboxed environments (gVisor- or Firecracker-class isolation) with CPU/memory/disk quotas, egress restrictions, and per-tenant network boundaries. **[I]**
- **Supply chain:** build images pinned by digest; upstream (qubic/core, AIO kit) updates staged through automated regression tests before rollout. **[I]**
- **Blast radius:** devnets are isolated from mainnet and from each other; no production core nodes are part of the service. **[I]**

## Audit plan
- **Before beta (M3/M4):** targeted third-party security review of multi-tenant isolation and sandbox escape, funded from the M3 tranche; findings fixed before paid tiers open. A scope beyond the tranche waits for revenue-funded review post-beta.
- **Ongoing:** annual re-test; dependency scanning in CI; public status and incident history.
- We deploy **no smart contracts of our own**, so the program's covered smart-contract audit (1 per project) is reserved for future contract work (e.g., if a template or registry contract is ever added). **[V - program term]**

## Dependencies
| Dependency | Risk | Mitigation |
|---|---|---|
| Official AIO kit / core-lite / test harness | Upstream changes; archiving precedent (Madrid kit archived 2026-07-22) | Pin versions; automated upgrade tests; contribute back; fallback to maintaining our own image build |
| Commodity cloud (VPS/K8s) | Price / availability | Multi-provider abstraction; spot pools for CI |
| GitHub integration | API / policy changes | Abstract provider layer; CLI fallback |
| Public faucet / testnet (qforge etc.) | External dependency for test funds | Our devnets have their own faucet; public faucet is an optional integration |

## Operational & commercial risks (with stop conditions)
*L = likelihood, I = impact.*

| Risk | L | I | Mitigation | Stop condition |
|---|---|---|---|---|
| Core team ships a hosted IDE/devnet | M | H | Partner/backend positioning; E4 check; offer to power their surface | Official hosted workspace announced with a roadmap date → pivot to devnet/CI backend or shelve |
| Willingness to pay fails | M-H | H | Validate before build (E1/E3/E2); event sponsorship floor | Fewer than 3 paid pilot commitments → fallback per research report §1 |
| Unit economics miss | M | M | Measure in E5; pooling, autosuspend, tick-rate tuning | Cost > 2× price of cheapest tier → re-architect or abandon |
| Sandbox escape / abuse | L-M | H | Hard isolation, quotas, egress limits; pre-beta audit | Any confirmed escape class → halt beta pending review |
| Developer inflow stalls | M | M | Diversify channels (grants, Nostromo, partners); keep costs variable | Fewer than 5 paying teams at month 12 → maintenance mode |
| Protocol / toolchain drift | M | L-M | Pinned images; regression suite; fast rollback | Two consecutive core releases break workspace creation > 48 h → pause paid plans |

## Incident response (basics)
- **Sev-1 (isolation/secrets):** isolate tenant workloads, preserve logs, notify affected users within 24 h, publish a post-mortem.
- **Sev-2 (availability):** status page update, rollback to last known-good image.
- Incident templates and runbooks live in [../data/](../data/).
