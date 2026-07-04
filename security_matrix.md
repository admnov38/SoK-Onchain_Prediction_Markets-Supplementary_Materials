# Cross-Protocol Security Matrix — readable view

Human-readable rendering of `security_matrix_worksheet.csv` (the machine-readable source). Scores are transcribed from Table 5 of the paper; justifications apply the Appendix A rubric. **3** = structurally mitigated, **2** = partial, **1** = fully vulnerable, **–** = N/A.

Legend: 🟢 3 mitigated · 🟡 2 partial · 🔴 1 vulnerable · ⚪ N/A

## Attack vectors

| Code | Vector | Code | Vector |
|---|---|---|---|
| **A1** | Oracle manipulation | **A8** | MEV |
| **A2** | Data source | **A9** | SC bugs |
| **A3** | Resolution front-running | **A10** | Flash loan |
| **A4** | Governance | **A11** | Insider |
| **A5** | Wash trading | **A12** | Censorship |
| **A6** | Outcome manipulation | **A13** | Griefing |
| **A7** | Price manipulation | **A14** | Rug pull |

## Score matrix

| Protocol | A1 | A2 | A3 | A4 | A5 | A6 | A7 | A8 | A9 | A10 | A11 | A12 | A13 | A14 | Σ |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Polymarket** | 🟡 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🔴 | 🟡 | 🟢 | 1.86 |
| **Kalshi** | 🟢 | 🟢 | ⚪ | ⚪ | 🟢 | 🟢 | 🟢 | ⚪ | ⚪ | ⚪ | 🟢 | 🔴 | ⚪ | 🟡 | 2.63 |
| **Augur v2** | 🟢 | 🟡 | 🟡 | 🟡 | 🔴 | 🔴 | 🔴 | 🔴 | 🟡 | 🟡 | 🔴 | 🟢 | 🔴 | 🟢 | 1.79 |
| **Gnosis/Omen** | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟡 | 🔴 | 🟡 | 🟡 | 🔴 | 🟢 | 🟡 | 🟢 | 1.93 |
| **Azuro** | 🟡 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 1.86 |
| **Zeitgeist** | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟢 | 🟡 | 🟡 | 1.93 |
| **Overtime** | 🟢 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟢 | 🔴 | 🟡 | 🟡 | 🟡 | 2.00 |
| **MetaDAO** | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🔴 | 🟢 | 🟡 | 🟡 | 1.93 |
| **Drift BET** | 🟡 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 1.86 |
| **Seer** | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟡 | 🔴 | 🟡 | 🟡 | 🔴 | 🟢 | 🟡 | 🟢 | 1.93 |
| **XO Market** | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟡 | 🔴 | 🔴 | 🟡 | 🔴 | 🟢 | 🟡 | 🟡 | 1.79 |
| **Rain** | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟡 | 🟡 | 🔴 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 1.79 |
| **Opinion** | 🟡 | 🟡 | 🔴 | 🔴 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟡 | 🔴 | 🔴 | 🟡 | 🟡 | 1.64 |
| **Limitless** | 🟡 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🔴 | 🟡 | 🟡 | 🟡 | 1.86 |

> Kalshi's Σ (2.63) is a mean over its 8 applicable vectors (6 are N/A for an off-chain venue).

## Findings (reproduced from this data)

- **Finding 1:** no protocol scores 3 on both censorship resistance (A12) and market integrity (A5–A7).
- **Finding 2:** resolution front-running (A3) is the most universally unmitigated vector — 6 of 13 on-chain protocols score 1 (Polymarket, Azuro, Overtime, Drift BET, Opinion, Limitless).
- **Finding 3:** MEV (A8) has no on-chain Score-3 protocol; Kalshi's off-chain matching makes it N/A.
- **Finding 4:** on-chain Σ clusters in [1.64, 2.00]; only the centralized benchmark Kalshi (2.63) sits above.

## Per-protocol detail

### Polymarket (Σ = 1.86)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | UMA optimistic oracle resolves Polymarket markets; token-weighted disputes give rho approx 0.2-0.4 at $7M, so a whale can force an incorrect resolution as in the March 2025 Ukraine-bet dispute. | [91,108,139] |
| A2 Data source | 2 | Resolution sources are specified per market but can rest on a single editable source; the November 2025 ISW map edit preceded a payout, showing source integrity is not guaranteed. | [38] |
| A3 Resolution front-running | 1 | On-chain CTF settlement means the UMA resolution transaction is visible in the public mempool while CLOB trading stays open, so searchers can capture the price-to-0/1 gap. | Appendix A rubric + architecture |
| A4 Governance | 2 | UMA governance is token-weighted but sits behind Snapshot-style voting and timelocks rather than being directly flash-loan exposed on the market contracts. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | No KYC on trading, but fee structure and behavioral detection exist; Sirolly et al. estimate ~25% of volume is artificial, consistent with partial rather than full mitigation. | [128] |
| A6 Outcome manipulation | 2 | Creation is curated (operator-listed markets) with limited insider surveillance rather than full monitoring, deterring but not eliminating outcome manipulation. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | Deep CLOB liquidity and position monitoring attenuate price manipulation, but there are no hard position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 2 | Off-chain order matching reduces on-chain sandwich surface, but settlement is on-chain and order flow leaks to the operator, so MEV is reduced not eliminated. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | Gnosis CTF and the exchange contracts are professionally audited with an active bounty, but none are formally verified. | [70,140] |
| A10 Flash loan | 2 | Thin FPMM/CLOB pools can be dislocated by a single-block flash loan, but core CTF split/merge conservation limits one-block drain, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with at most post-hoc analysis and no identity-linked insider surveillance leaves insider trading essentially unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 1 | Operator-controlled off-chain matching and discretionary market removal let Polymarket halt, remove, or block markets, so censorship resistance is minimal (score reduced to 1). | Appendix A rubric + architecture |
| A13 Griefing | 2 | Curated creation plus deposits deter mass spam-market griefing without a formal bond, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 3 | Non-custodial CTF collateral with immutable, audited core contracts means users retain custody and there are no admin keys to rug funds. | [70] |

### Kalshi (Σ = 2.63)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 3 | As a CFTC-regulated exchange, resolution is by a licensed operator whose corruption cost far exceeds any market-size profit, giving rho>1 (the regulated-operator anchor of the rubric). | [80,146,148] |
| A2 Data source | 3 | Contract terms and settlement sources are unambiguous and legally specified under CFTC oversight, satisfying the multi-source/verifiable criterion. | [80,146,148] |
| A3 Resolution front-running | – | off-chain/centralized architecture: vector not applicable | Appendix A rubric + architecture |
| A4 Governance | – | off-chain/centralized architecture: vector not applicable | Appendix A rubric + architecture |
| A5 Wash trading | 3 | Mandatory KYC/CIP on every account prevents Sybil identities, the rubric's canonical Score-3 condition for wash trading. | [80] |
| A6 Outcome manipulation | 3 | Curated, regulator-approved contract listing plus market surveillance obligations deter manipulation of the underlying outcome. | [80,146,148] |
| A7 Price manipulation | 3 | Federally mandated position limits combined with a regulated central book give the position-limits-plus-liquidity Score-3 condition. | [80,148] |
| A8 MEV | – | off-chain/centralized architecture: vector not applicable | Appendix A rubric + architecture |
| A9 SC bugs | – | off-chain/centralized architecture: vector not applicable | Appendix A rubric + architecture |
| A10 Flash loan | – | off-chain/centralized architecture: vector not applicable | Appendix A rubric + architecture |
| A11 Insider | 3 | Regulated-exchange trade surveillance and enforcement of insider-trading rules satisfy the surveillance-plus-enforcement condition. | [80,146] |
| A12 Censorship | 1 | A single licensed operator fully controls listing and access and can halt, remove, or block any market, so censorship resistance is minimal. | Appendix A rubric + architecture |
| A13 Griefing | – | off-chain/centralized architecture: vector not applicable | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Custodial fiat balances held by the operator, mitigated by CFTC custody/segregation rules rather than by non-custodial code, giving partial (2) rather than full mitigation. | Appendix A rubric + architecture |

### Augur v2 (Σ = 1.79)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 3 | The REP fork mechanism lets honest holders migrate to a correct universe, making corruption cost exceed manipulation profit (rho>1); the June-Aug 2026 Augur Fork exercised exactly this path. | [89,111] |
| A2 Data source | 2 | Reporters resolve against specified market terms with dispute rounds, but the free-text source can be ambiguous, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 2 | Multi-round reporting and dispute windows give limited pre-publication visibility of the final outcome rather than an instantly public resolution tx. | Appendix A rubric + architecture |
| A4 Governance | 2 | REP-weighted governance is behind fork/dispute timelocks rather than being directly flash-loan exposed, giving partial mitigation. | Appendix A rubric + architecture |
| A5 Wash trading | 1 | Permissionless on-chain trading with no identity layer and no built-in wash-trading detection leaves Sybil trading unmitigated. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 1 | Fully permissionless market creation with no outcome-surveillance monitoring maximizes outcome-manipulation exposure. | Appendix A rubric + architecture |
| A7 Price manipulation | 1 | Thin AMM/order-book liquidity with no position limits leaves prices manipulable, matching the demonstrated-thin-market condition. | Appendix A rubric + architecture |
| A8 MEV | 1 | Fully on-chain order placement in a public mempool is directly sandwichable, the Score-1 MEV condition. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | Augur v2 contracts are professionally audited with a bounty program but are not formally verified. | [140] |
| A10 Flash loan | 2 | Core reporting is not one-block exploitable, but thin trading pools can be dislocated by flash loans, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous reporters and traders with no insider surveillance leave insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 3 | Fully permissionless, immutable contracts with multiple possible frontends mean no operator can halt or remove markets. | Appendix A rubric + architecture |
| A13 Griefing | 1 | Low-cost permissionless market creation lets spurious markets dilute reporting resources (parasitic markets), approaching zero-cost griefing. | [110] |
| A14 Rug pull | 3 | Non-custodial, immutable, audited contracts with no admin keys mean funds cannot be rugged. | [140] |

### Gnosis/Omen (Σ = 1.93)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | Omen relies on a bonded escalation (Reality.eth/Kleros) oracle whose dispute economics give rho in the partial range rather than the fork-level guarantee. | Appendix A rubric + architecture |
| A2 Data source | 2 | Questions are specified with an arbitration fallback for edge cases via Reality.eth disputes, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 2 | Reality.eth answer submission has a bounded challenge window, giving limited pre-publication visibility rather than an instantly settled public tx. | Appendix A rubric + architecture |
| A4 Governance | 2 | DAO/arbitrator governance is token-weighted but sits behind dispute timelocks rather than being directly flash-loan exposed. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | Permissionless FPMM trading with no identity layer but LP-fee friction gives only partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 1 | Permissionless market creation with no outcome surveillance leaves outcome manipulation unmitigated. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | FPMM curvature and LP depth provide moderate liquidity but no position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 1 | On-chain FPMM swaps in a public mempool are sandwichable, the Score-1 MEV condition. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | The Gnosis Conditional Tokens Framework was audited (ERC-1155 reentrancy and collection-id collisions remediated) with a bounty, but is not formally verified. | [70,140] |
| A10 Flash loan | 2 | CTF split/merge conservation blocks one-block drain of the core, but thin FPMM pools remain flash-loan dislocatable, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 3 | Permissionless, immutable CTF/FPMM contracts with independent frontends mean no operator can halt or remove markets. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Permissionless creation with a deposit/LP cost deters mass spam without a formal bond, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 3 | Non-custodial, immutable, audited CTF contracts with no admin keys mean funds cannot be rugged. | [70] |

### Azuro (Σ = 1.86)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | Azuro uses a specified data-feed/oracle for sports outcomes whose manipulation resistance sits in the partial rho range rather than at fork/regulator level. | Appendix A rubric + architecture |
| A2 Data source | 2 | Sports results are relatively unambiguous but rest on a specified provider with dispute handling, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 1 | The on-chain resolution transaction is public while pool trading stays open, so searchers can capture the price-to-0/1 gap. | Appendix A rubric + architecture |
| A4 Governance | 2 | DAO governance is token-weighted behind Snapshot-style voting and a timelock rather than directly flash-loan exposed. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | Permissionless betting with no identity layer but fee/stake friction gives partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 2 | Sports outcomes are curated to established events with limited surveillance, giving partial outcome-manipulation mitigation. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | Liquidity-tree pooled liquidity provides moderate depth but no hard position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 2 | Off-chain-assisted order routing reduces but does not eliminate on-chain MEV, giving partial mitigation. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | Azuro protocol contracts carry a professional audit and active bounty but are not formally verified. | Appendix A rubric + architecture |
| A10 Flash loan | 2 | Pooled liquidity is not drainable in a single block, but short-window exposure remains, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous betting with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 2 | Core contracts are permissionless but the primary frontend is operator-run, giving partial censorship resistance. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Permissionless creation with a deposit deters mass spam-market griefing, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Non-custodial core with upgradable components behind a timelock gives partial rug-pull protection. | Appendix A rubric + architecture |

### Zeitgeist (Σ = 1.93)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | Zeitgeist's Rikiddo/court oracle resolves via a bonded dispute court whose economics give rho in the partial range. | Appendix A rubric + architecture |
| A2 Data source | 2 | Questions are specified with a dispute-court fallback for edge cases, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 2 | Court resolution has a bounded challenge/appeal window giving limited pre-publication visibility rather than an instant public settlement. | Appendix A rubric + architecture |
| A4 Governance | 2 | On-chain (Substrate) governance is token-weighted behind referenda timelocks rather than directly flash-loan exposed. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | Permissionless trading with no identity layer but fee/stake friction gives partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 1 | Permissionless market creation with no outcome surveillance leaves outcome manipulation unmitigated. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | Rikiddo AMM depth gives moderate liquidity but no position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 2 | Substrate block production without a public EVM mempool reduces sandwiching, giving partial MEV mitigation. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | Zeitgeist pallet code carries a professional audit and bounty but is not formally verified. | Appendix A rubric + architecture |
| A10 Flash loan | 2 | AMM core is not one-block drainable but short-window exposure remains, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 3 | Permissionless on-chain markets with immutable pallet logic and open access mean no operator can halt or remove them. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Permissionless creation with a bond/deposit deters mass spam-market griefing, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Non-custodial core with upgradable runtime behind governance timelock gives partial rug-pull protection. | Appendix A rubric + architecture |

### Overtime (Σ = 2.00)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 3 | Overtime resolves sports markets against Chainlink feeds, whose decentralized reporting pushes manipulation cost above market size (rho>1) for the covered outcomes. | Appendix A rubric + architecture |
| A2 Data source | 2 | Sports results come from a specified Chainlink data feed with dispute handling, giving partial mitigation on ambiguous edge cases. | Appendix A rubric + architecture |
| A3 Resolution front-running | 1 | The on-chain resolution transaction is public while AMM trading stays open, so searchers can capture the price-to-0/1 gap. | Appendix A rubric + architecture |
| A4 Governance | 2 | DAO governance is token-weighted behind Snapshot voting and a timelock rather than directly flash-loan exposed. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | Permissionless betting with no identity layer but fee/stake friction gives partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 2 | Sports outcomes are curated to established events with limited surveillance, giving partial outcome-manipulation mitigation. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | AMM liquidity provides moderate depth but no hard position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 2 | Off-chain-assisted routing reduces but does not eliminate on-chain MEV, giving partial mitigation. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | Overtime/Thales contracts carry a professional audit and active bounty but are not formally verified. | Appendix A rubric + architecture |
| A10 Flash loan | 3 | Core sports-AMM operations are not exploitable in a single block, satisfying the one-block-safe Score-3 condition. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous betting with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 2 | Core contracts are permissionless but the primary frontend is operator-run, giving partial censorship resistance. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Permissionless creation with a deposit deters mass spam-market griefing, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Non-custodial core with upgradable components behind a timelock gives partial rug-pull protection. | Appendix A rubric + architecture |

### MetaDAO (Σ = 1.93)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | MetaDAO's futarchy decides via multi-day TWAP over conditional markets, whose sustained-capital cost places oracle-manipulation resistance in the partial rho range. | [97,75] |
| A2 Data source | 2 | Proposal outcomes are defined by conditional-market prices with specified resolution but residual ambiguity, giving partial mitigation. | [97] |
| A3 Resolution front-running | 2 | Multi-day TWAP settlement gives limited pre-publication visibility of the decisive price rather than an instantly public resolution tx. | Appendix A rubric + architecture |
| A4 Governance | 2 | Futarchy replaces token-vote governance with market decision behind multi-day windows, so it is not directly flash-loan exposed, giving partial mitigation. | [75,97] |
| A5 Wash trading | 2 | Permissionless conditional-market trading with no identity layer but fee/stake friction gives partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 2 | Proposal-scoped market creation with some curation and limited surveillance gives partial outcome-manipulation mitigation. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | Conditional-market liquidity gives moderate depth but no position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 2 | Solana execution without a public EVM mempool reduces sandwiching, giving partial MEV mitigation. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | MetaDAO futarchy contracts carry a professional audit and bounty but are not formally verified. | Appendix A rubric + architecture |
| A10 Flash loan | 1 | Multi-day futarchy TWAPs are by construction resistant to single-block manipulation, but sustained-capital reflexivity remains, so the exposure is scored fully vulnerable to one-block-style capital attack on the AMM leg. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 3 | Permissionless on-chain conditional markets with immutable program logic and open access mean no operator can halt or remove them. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Proposal-bonded market creation deters mass spam, giving partial griefing mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Non-custodial core with upgradable program authority behind governance gives partial rug-pull protection. | Appendix A rubric + architecture |

### Drift BET (Σ = 1.86)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | Drift BET resolves via a specified oracle whose manipulation resistance sits in the partial rho range rather than at fork/regulator level. | Appendix A rubric + architecture |
| A2 Data source | 2 | Outcomes rest on a specified data source with dispute handling for edge cases, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 1 | The on-chain resolution transaction is visible while CLOB trading stays open, so searchers can capture the price-to-0/1 gap. | Appendix A rubric + architecture |
| A4 Governance | 2 | DAO governance is token-weighted behind voting and a timelock rather than directly flash-loan exposed. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | Permissionless trading with no identity layer but fee/stake friction gives partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 2 | Curated market creation with limited surveillance gives partial outcome-manipulation mitigation. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | Drift's order-book liquidity provides moderate depth but no hard position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 2 | Solana execution without a public EVM mempool reduces sandwiching, giving partial MEV mitigation. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | Drift program code carries a professional audit and active bounty but is not formally verified. | Appendix A rubric + architecture |
| A10 Flash loan | 2 | Core order-book operations are not one-block drainable but short-window exposure remains, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 2 | Core program is permissionless but the primary frontend is operator-run, giving partial censorship resistance. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Permissionless creation with a deposit deters mass spam-market griefing, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Non-custodial core with upgradable program authority behind a timelock gives partial rug-pull protection. | Appendix A rubric + architecture |

### Seer (Σ = 1.93)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | Seer resolves via a bonded escalation (Reality.eth/Kleros) oracle whose dispute economics give rho in the partial range. | Appendix A rubric + architecture |
| A2 Data source | 2 | Questions are specified with an arbitration fallback for edge cases, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 2 | Bonded-answer submission has a challenge window giving limited pre-publication visibility rather than an instant public settlement. | Appendix A rubric + architecture |
| A4 Governance | 2 | Governance is token-weighted behind dispute/arbitration timelocks rather than directly flash-loan exposed. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | Permissionless trading with no identity layer but fee/stake friction gives partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 1 | Permissionless market creation with no outcome surveillance leaves outcome manipulation unmitigated. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | Pooled/CTF liquidity gives moderate depth but no position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 1 | On-chain swaps in a public mempool are sandwichable, the Score-1 MEV condition. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | Seer uses audited Gnosis CTF-derived contracts with a bounty but wrapper code adds trust and it is not formally verified. | [70,140] |
| A10 Flash loan | 2 | CTF conservation blocks one-block core drain but thin pools remain flash-loan dislocatable, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 3 | Permissionless, immutable CTF-based contracts with independent frontends mean no operator can halt or remove markets. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Permissionless creation with a deposit deters mass spam-market griefing, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 3 | Non-custodial, immutable, audited CTF core with no admin keys means funds cannot be rugged. | [70] |

### XO Market (Σ = 1.79)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | XO Market resolves via a bonded/escalation oracle whose dispute economics give rho in the partial range. | Appendix A rubric + architecture |
| A2 Data source | 2 | Questions are specified with a dispute fallback for edge cases, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 2 | Bonded resolution has a challenge window giving limited pre-publication visibility rather than an instant public settlement. | Appendix A rubric + architecture |
| A4 Governance | 2 | Governance is token-weighted behind dispute timelocks rather than directly flash-loan exposed. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | Permissionless trading with no identity layer but fee/stake friction gives partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 1 | Permissionless market creation with no outcome surveillance leaves outcome manipulation unmitigated. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | LS-LMSR liquidity gives moderate depth but no position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 1 | On-chain swaps in a public mempool are sandwichable, the Score-1 MEV condition. | Appendix A rubric + architecture |
| A9 SC bugs | 1 | XO Market contracts lack a public audit or bounty, matching the no-audit Score-1 condition. | Appendix A rubric + architecture |
| A10 Flash loan | 2 | AMM core is not one-block drainable but short-window exposure remains, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 3 | Permissionless on-chain markets with immutable logic and open access mean no operator can halt or remove them. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Permissionless creation with a deposit deters mass spam-market griefing, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Non-custodial core with upgradable components behind a timelock gives partial rug-pull protection. | Appendix A rubric + architecture |

### Rain (Σ = 1.79)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | Rain resolves via a specified Chainlink-backed oracle whose manipulation resistance sits in the partial rho range. | Appendix A rubric + architecture |
| A2 Data source | 2 | Outcomes rest on a specified data source with dispute handling for edge cases, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 2 | Bonded/limited-visibility resolution gives limited pre-publication visibility rather than an instant public settlement. | Appendix A rubric + architecture |
| A4 Governance | 2 | Governance is token-weighted behind voting and a timelock rather than directly flash-loan exposed. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | Permissionless trading with no identity layer but fee/stake friction gives partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 1 | Permissionless market creation with no outcome surveillance leaves outcome manipulation unmitigated. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | AMM liquidity gives moderate depth but no position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 2 | Off-chain-assisted routing reduces but does not eliminate on-chain MEV, giving partial mitigation. | Appendix A rubric + architecture |
| A9 SC bugs | 1 | Rain contracts lack a public audit or bounty, matching the no-audit Score-1 condition. | Appendix A rubric + architecture |
| A10 Flash loan | 2 | AMM core is not one-block drainable but short-window exposure remains, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 2 | Core contracts are permissionless but the primary frontend is operator-run, giving partial censorship resistance. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Permissionless creation with a deposit deters mass spam-market griefing, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Non-custodial core with upgradable components behind a timelock gives partial rug-pull protection. | Appendix A rubric + architecture |

### Opinion (Σ = 1.64)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | Opinion resolves via a specified AI-assisted oracle whose manipulation resistance sits in the partial rho range rather than at fork/regulator level. | Appendix A rubric + architecture |
| A2 Data source | 2 | Outcomes rest on a specified source with dispute handling for edge cases, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 1 | The on-chain resolution transaction is public while CLOB trading stays open, so searchers can capture the price-to-0/1 gap. | Appendix A rubric + architecture |
| A4 Governance | 1 | Governance is operator/token-controlled and directly exposed rather than protected by a >24h timelock, matching the flash-loan-exposed Score-1 condition. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | No-KYC trading with rewards for larger trades gives incentives for wash trading; ~14% of wallets and 45% of all-time sports volume are flagged suspicious, but fee/reward friction keeps it at partial (2). | [49] |
| A6 Outcome manipulation | 2 | Curated creation with limited surveillance gives partial outcome-manipulation mitigation. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | CLOB liquidity gives moderate depth but no hard position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 2 | Off-chain-assisted matching reduces but does not eliminate on-chain MEV, giving partial mitigation. | Appendix A rubric + architecture |
| A9 SC bugs | 1 | Opinion contracts lack a public audit or bounty, matching the no-audit Score-1 condition. | Appendix A rubric + architecture |
| A10 Flash loan | 2 | Core operations are not one-block drainable but short-window exposure remains, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 1 | Operator-controlled matching and market removal let Opinion halt, remove, or block markets, so censorship resistance is minimal. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Curated creation with a deposit deters mass spam-market griefing, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Non-custodial core with upgradable components behind a timelock gives partial rug-pull protection. | Appendix A rubric + architecture |

### Limitless (Σ = 1.86)

| Vector | Score | Justification | Evidence |
|---|:-:|---|---|
| A1 Oracle manipulation | 2 | Limitless resolves via a specified oracle whose manipulation resistance sits in the partial rho range rather than at fork/regulator level. | Appendix A rubric + architecture |
| A2 Data source | 2 | Outcomes rest on a specified source with dispute handling for edge cases, giving partial mitigation. | Appendix A rubric + architecture |
| A3 Resolution front-running | 1 | The on-chain (Base) resolution transaction is public while CLOB trading stays open, so searchers can capture the price-to-0/1 gap. | Appendix A rubric + architecture |
| A4 Governance | 2 | Governance is token-weighted behind voting and a timelock rather than directly flash-loan exposed. | Appendix A rubric + architecture |
| A5 Wash trading | 2 | Permissionless trading with no identity layer but fee/stake friction gives partial wash-trading deterrence. | Appendix A rubric + architecture |
| A6 Outcome manipulation | 2 | Curated market creation with limited surveillance gives partial outcome-manipulation mitigation. | Appendix A rubric + architecture |
| A7 Price manipulation | 2 | CLOB liquidity gives moderate depth but no hard position limits, giving partial mitigation. | Appendix A rubric + architecture |
| A8 MEV | 2 | Off-chain-assisted matching reduces but does not eliminate on-chain MEV, giving partial mitigation. | Appendix A rubric + architecture |
| A9 SC bugs | 2 | Limitless contracts carry a professional audit and bounty but are not formally verified. | Appendix A rubric + architecture |
| A10 Flash loan | 2 | Core operations are not one-block drainable but short-window exposure remains, giving partial resistance. | Appendix A rubric + architecture |
| A11 Insider | 1 | Pseudonymous trading with no insider surveillance leaves insider activity unmonitored. | Appendix A rubric + architecture |
| A12 Censorship | 2 | Core contracts are permissionless but the primary frontend is operator-run, giving partial censorship resistance. | Appendix A rubric + architecture |
| A13 Griefing | 2 | Permissionless creation with a deposit deters mass spam-market griefing, giving partial mitigation. | Appendix A rubric + architecture |
| A14 Rug pull | 2 | Non-custodial core with upgradable components behind a timelock gives partial rug-pull protection. | Appendix A rubric + architecture |
