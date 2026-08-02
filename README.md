# stellar-bet-contracts

> Soroban smart contracts powering the StellarBet prediction market platform.

[![Stellar Wave Program](https://img.shields.io/badge/Stellar%20Wave-Active-blue?logo=stellar)](https://drips.network/wave)
[![Built on Soroban](https://img.shields.io/badge/Built%20on-Soroban-blueviolet)](https://stellar.org/soroban)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

## Contracts

| Contract | Description |
|---|---|
| `betting_pool` | Core bet lifecycle: place, settle, claim, cancel |
| `odds_oracle` | Multi-sig oracle that settles markets from off-chain results |
| `house_escrow` | Liquidity pool: LPs deposit XLM, earn protocol fees |
| `bet_token` | SEP-41 BET governance/rewards token |

## Architecture

```
User → BettingPool.place_bet()
                ↓
         HouseEscrow (holds liquidity)
                ↑
OddsOracle.report_result() ← Off-chain oracle service
                ↓
BettingPool.settle_market()
                ↓
User → BettingPool.claim_payout()
         → HouseEscrow.pay_winner()
```

## Prerequisites

- [Rust + wasm32 target](https://doc.rust-lang.org/book/ch01-01-installation.html)
- [Stellar CLI](https://developers.stellar.org/docs/tools/stellar-cli)

```bash
rustup target add wasm32-unknown-unknown
cargo install stellar-cli --features opt
```

## Getting Started

```bash
# Clone
git clone https://github.com/YOUR_ORG/stellar-bet-contracts
cd stellar-bet-contracts

# Build all contracts
make build

# Run tests
make test

# Generate TypeScript bindings (for frontend)
make bindings

# Deploy to testnet
stellar keys generate admin --network testnet --fund
make deploy-all ADMIN_ID=admin NETWORK=testnet
```

## Contract Addresses (Testnet)

> Update these after deployment.

| Contract | Testnet Address |
|---|---|
| BettingPool | `TBD` |
| OddsOracle | `TBD` |
| HouseEscrow | `TBD` |
| BetToken | `TBD` |

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md). This repo participates in the
[Stellar Wave Program](https://drips.network/wave) — open issues are tagged
`stellar-wave` and carry point rewards.

## Security

This is **testnet software**. Do not use with real funds until a full audit is complete.
See [SECURITY.md](./SECURITY.md) for responsible disclosure.

## License

MIT
