# Team

> **Note:** GitHub profiles verified Oct 2026 (links below **[V]**). Role assignments are proposed from that public evidence; legal names, commitment windows and IP confirmations must be completed before submission **[FILL]**.

## Roles and commitment

| Role | Name | Relevant experience | Commitment | Ownership |
|---|---|---|---|---|
| Systems & infrastructure engineer (co-founder) | **Qeyphen** — [github.com/Qeyphen](https://github.com/Qeyphen) (display name "Kifen") | Systems programmer, "correctness first" (Rust/C/C++, ROS2, Linux). Shipped **Vmctl** — a KVM VM provision/run/control plane over an async-Rust control plane, directly analogous to QuIDE's sandbox/devnet lifecycle ([Vmctl](https://github.com/Qeyphen/Vmctl)); **mujoco-verification-environments** — headless automated grading and numerical-stability tracking infrastructure ([repo](https://github.com/Qeyphen/mujoco-verification-environments)); **sebi** — deterministic static analysis and preflight safety checks for smart contracts ([sebi](https://github.com/Qeyphen/sebi)); bare-metal STM32 firmware, crypto primitives, packet-level networking tooling **[V]** | Full-time from M1 **[FILL: confirm]** | Committed founder |
| Product & full-stack engineer — editor & UX (co-founder) | **zynorr** — [github.com/zynorr](https://github.com/zynorr) (display name "zynor") | Developer-tooling and web3 product engineer (TypeScript/React, 48 public repos). Shipped **hardhat-starknet** — a Hardhat plugin with local devnet support and clean deploy/call workflows, the closest published analog to QuIDE's devnet-in-browser flow ([repo](https://github.com/zynorr/hardhat-starknet)); **ascendkit** — SDK, simulator, decoders and CLI for a contract platform ([repo](https://github.com/zynorr/ascendkit)); **varatrace** — async message-trace viewer for a smart-contract chain ([repo](https://github.com/zynorr/varatrace)); **cell-sandbox** — a browser workspace (Next.js/React/TypeScript, Vitest-tested) for the Nervos CKB cell model with guided flows to design cells, inspect state transitions and build wallet-signed transactions ([repo](https://github.com/zynorr/cell-sandbox), [live demo](https://cell-sandbox-m.vercel.app)); x402 payment middleware and offchain-data starter kits, relevant to Qubic's x402 payments track **[V]** | Full-time from M1 **[FILL: confirm]** | Committed founder |
| C++ / Qubic advisor | **[FILL]** | Qubic contract development (QPI restrictions, GoogleTest harness, contract-verify, lifecycle); [FILL: contracts contributed / relevant work]. Systems/C++ depth is covered in-house by Qeyphen; this role is strictly the Qubic-domain gap. | ≈0.15 FTE consulting | Contractor |
| Product design | **[FILL]** | Dev-tool UX, brand; [FILL] | Part-time | Contractor |

## Ownership and IP
- All code produced under this project is owned by the company/team and will be licensed per the program's requirements; open-source upstream components (qubic core, AIO kit, libraries) remain under their own licenses — inventory maintained in [../data/](../data/).
- No conflicting employment or IP claims: **[FILL: confirm per person]**.

## Why this team
- **Qeyphen** builds exactly the layer QuIDE depends on: VM provisioning and lifecycle control ([Vmctl](https://github.com/Qeyphen/Vmctl)), headless automated test infrastructure ([mujoco-verification-environments](https://github.com/Qeyphen/mujoco-verification-environments)), and static analysis for smart contracts ([sebi](https://github.com/Qeyphen/sebi)) — Linux-native systems software in C/C++/Rust that maps directly to sandbox orchestration, the C++ contract toolchain and CI. **[V]**
- **zynorr** has shipped developer tooling for contract platforms end to end: a devnet-enabled Hardhat plugin with deploy/call flows ([hardhat-starknet](https://github.com/zynorr/hardhat-starknet)), integrator kits with SDK/simulator/CLI ([ascendkit](https://github.com/zynorr/ascendkit)), a chain message-trace viewer ([varatrace](https://github.com/zynorr/varatrace)) and a full browser workspace with visual transaction design, inspection and wallet-signed construction ([cell-sandbox](https://github.com/zynorr/cell-sandbox)) — mapping to QuIDE's editor/UX, workspace flows and deploy experience, plus payments rails relevant to Qubic's x402 work. **[V]**
- Advisor coverage on the Qubic-specific stack (QPI restrictions, contract testing harness, contract lifecycle) via the ≈0.15 FTE consultant **[FILL: identify]**.
- Neither founder has public Qubic-specific contract work; that domain gap is covered by the advisor and de-risked by the E5 prototype spike. **[I]**

## Hiring & compensation plan
- No hires within the program: both co-founders build; the C++/Qubic advisor (≈0.15 FTE) and a part-time designer are contracted — budget in [09-milestones-budget.md](09-milestones-budget.md).
- Founder pay is a below-market stipend within the $30K budget; the difference is deferred and recovered only through the revenue-share return ([08-return-to-incubation.md](08-return-to-incubation.md)). **[I]** **[FILL: confirm]**
- First external hire only after paying revenue or follow-on funding. **[I]**
