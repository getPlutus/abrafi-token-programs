# AbraFi Token Programs

Solana smart contracts for the AbraFi protocol, built with [Anchor](https://www.anchor-lang.com/) 0.32.x.

## Programs

| Program                  | Description                                                                                                                                    |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `usdaf`                  | Collateral-backed stablecoin. Users deposit USDC/USDT and receive USDAF.                                                                       |
| `susdaf`                 | Yield-bearing wrapper. Users stake USDAF and receive sUSDAF. Yield accrues via exchange rate appreciation.                                     |
| `abrafi-backed-token`    | Generalised collateral-backed token program, redeployable for future tokens.                                                                   |
| `abrafi-staking-rewards` | In-kind claimable rewards staking. Stake a token, earn more of the same token.                                                                 |
| `abrafi-yield-router`    | Receives yield tokens and distributes them proportionally to registered recipients based on live token balances.                               |
| `reward-distributor`     | Per-season Merkle-based reward distributor. Claimants prove eligibility via Merkle proof and receive tokens routed through a vesting schedule. |
| `vesting`                | Vesting schedule program used as the destination in the reward distributor claim flow.                                                         |
| `staking`                | Simple stake-only program used as a vesting destination. No unstake, no rewards.                                                               |

## Building

```bash
# Install Rust (see https://rustup.rs)
# Install Solana CLI (see https://docs.solanalabs.com/cli/install)
# Install Anchor CLI (see https://www.anchor-lang.com/docs/installation)

# Build all programs
anchor build
```

## Verified Builds

All programs deployed on mainnet are built using [solana-verify](https://github.com/Ellipsis-Labs/solana-verify) for reproducible, verifiable builds. You can verify any deployed program matches this source code:

```bash
# Install solana-verify
cargo install solana-verify

# Build reproducibly
solana-verify build --library-name <program_name>

# Verify against a deployed program
solana-verify verify-from-repo \
  -u https://api.mainnet-beta.solana.com \
  --program-id <PROGRAM_ID> \
  https://github.com/getPlutus/abrafi-token-programs \
  --commit-hash <COMMIT_HASH> \
  --library-name <program_name> \
  --mount-path programs/<program_name>
```

Program IDs and verified commit hashes for each release are published in the [releases](../../releases) page.

## Program Upgrade Governance

Program upgrades are gated behind a [Squads v4](https://squads.so) multisig. No single keypair can upgrade a program unilaterally — a threshold of members must approve each proposal before the upgrade executes.

## Security

To report a vulnerability, please email **<security@abrafi.com>**.

Do not open a public GitHub issue for security vulnerabilities.

## License

[Add your license here]
