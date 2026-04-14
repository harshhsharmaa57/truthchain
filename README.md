# TruthChain

> **Stake XLM on what you believe to be true. The chain decides.**

Post a statement. Stake XLM. Others support it (agree) or challenge it (disagree). After 30 days (~17,280 Stellar ledgers), anyone resolves it — whichever side staked more wins. Every action is an on-chain Soroban transaction.

---

## Live Links

| | |
|---|---|
| **Frontend** | `https://truthchain-app.vercel.app` |
| **Contract** | `https://stellar.expert/explorer/testnet/contract/CCK3JWE6YTW7X22E3LPBCYWZMMST6G4V3U3AEQU66V4QLJF7NKGMI34X` |

---

## Why This Project Matters

This project turns a familiar real-world workflow into a verifiable on-chain primitive on Stellar: transparent state transitions, user-authenticated actions, and deterministic outcomes.

## Architecture

- **Smart Contract Layer**: Soroban contract enforces business rules, authorization, and state transitions.
- **Client Layer**: React + Vite frontend handles wallet UX, transaction composition, and real-time status views.
- **Wallet/Auth Layer**: Freighter signs every state-changing action so operations are attributable and non-repudiable.
- **Infra Layer**: Stellar Testnet + Soroban RPC for execution; Vercel for frontend hosting.
## Contract Functions

```rust
post_statement(author, text, stake: i128, xlm_token) -> u64
challenge(challenger, statement_id, stake: i128, xlm_token)
support(supporter, statement_id, stake: i128, xlm_token)
resolve(statement_id)            // anyone calls after expiry
get_statement(id) -> Statement
get_recent()      -> Vec<u64>
count()           -> u64
```

---

## Run Locally

```bash
chmod +x scripts/deploy.sh && ./scripts/deploy.sh
cd frontend && npm install && npm run dev
```



