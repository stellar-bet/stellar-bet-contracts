# Contributing to stellar-bet-contracts

Thanks for contributing! This repo is part of the **Stellar Wave Program** —
open issues carry XLM point rewards. Here's everything you need to get started.

## Stellar Wave Program

This repo participates in [Drips Wave](https://drips.network/wave), a weekly
contribution sprint run by the Stellar Development Foundation.

- Browse open issues tagged [`stellar-wave`](../../issues?q=label%3Astellar-wave)
- Apply via the Drips Wave app — **do not** comment "I'll take this" on the issue
- Once accepted, you'll be assigned and a due date is set
- Merge earns you Points redeemable for XLM from the SDF reward pool

## Prerequisites

```bash
# Rust toolchain
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup target add wasm32-unknown-unknown

# Stellar CLI
cargo install stellar-cli --features opt

# Verify
stellar --version
```

## Local Setup

```bash
git clone https://github.com/YOUR_ORG/stellar-bet-contracts
cd stellar-bet-contracts

# Build all contracts
make build

# Run tests
make test
```

## Workflow

1. Fork the repo and create a branch: `git checkout -b feat/your-feature`
2. Make your changes — keep each PR focused on one issue
3. Run `make test` — all tests must pass
4. Run `cargo fmt --all` and `cargo clippy` — zero warnings
5. Open a PR against `main` with the issue number in the title

## PR Requirements

- [ ] All existing tests pass (`make test`)
- [ ] New functionality has tests
- [ ] `cargo fmt --all` applied
- [ ] `cargo clippy -- -D warnings` clean
- [ ] PR description references the issue: `Closes #N`
- [ ] No `unwrap()` in production paths — use `expect("descriptive message")` or proper error handling

## Contract Safety Rules

- Never remove existing storage keys (breaks existing deployments)
- All auth checks must come before any state mutation
- Overflow: use `checked_mul` / `checked_add` for arithmetic on `i128`
- Do not add `unsafe` blocks

## Code Style

- Follow Rust idioms: prefer `match` over long `if/else` chains
- Comment public functions with `///` doc comments
- Keep contract methods under ~80 lines; extract helpers

## Issue Labels

| Label | Meaning |
|---|---|
| `stellar-wave` | Eligible for Wave point reward |
| `good-first-issue` | Suitable for first-time contributors |
| `bug` | Something is broken |
| `enhancement` | New feature or improvement |
| `security` | Security-related — see SECURITY.md |

## Questions?

Open a [discussion](../../discussions) or join the
[Stellar Discord](https://discord.gg/stellardev) `#soroban` channel.
