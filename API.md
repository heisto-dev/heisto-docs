# API reference

The implementation in heisto-app/server/src/app.ts is authoritative. JSON errors intentionally omit private validation details. API responses use no-store where configured. No public endpoint exposes wallet private keys, plaintext private challenge configuration or provider credentials.

## Route inventory
| Method | Path |
| --- | --- |
| GET | `/api/health` |
| GET | `/health` |
| GET | `/api/config` |
| GET | `/api/sentinels` |
| GET | `/api/sentinels/:id` |
| POST | `/api/sentinels/prepare` |
| POST | `/api/sentinels/confirm` |
| POST | `/api/sentinels/:id/tx` |
| POST | `/api/sentinels/:id/sync` |
| POST | `/api/attacks/prepare` |
| POST | `/api/attacks/submit` |
| GET | `/api/attacks/:pda` |
| POST | `/api/attacks/:pda/refund-tx` |
| POST | `/api/tx/send` |
| GET | `/api/leaderboard` |
| GET | `/api/profile/:wallet` |
| GET | `/api/shield/:id` |
| POST | `/api/shield/:id/advice` |
| POST | `/api/guard/score` |
| GET | `/api/practice/templates` |
| GET | `/api/practice/limits` |
| POST | `/api/practice` |
| POST | `/api/guard/keys` |
| GET | `/api/guard/keys` |
| DELETE | `/api/guard/keys/:id` |
| POST | `/v1/guard` |

## Core requests
- POST /api/sentinels/prepare: owner, name, publicInstructions, privateInstructions, goal, juryPrompt, optional canary, model, difficulty, poolSol, feeSol, optional compatible custom provider configuration. Returns id, pda, tx (unsigned versioned transaction).
- POST /api/sentinels/confirm: id and signature. Confirms chain state and instruction commitment before activating the existing draft.
- POST /api/sentinels/:id/tx: wallet and action (fund/claim/deactivate/withdraw), plus funding amount when applicable. Returns an unsigned transaction; chain owner checks are the spending boundary.
- POST /api/attacks/prepare: sentinelId, attacker and prompt. Returns fee/Attack address/unsigned transaction.
- POST /api/attacks/submit: attackPda, prompt and request signature. Checks the recorded escrow before execution and settlement.
- POST /api/attacks/:pda/refund-tx: returns an unsigned refund transaction for the eligible attacker.
- POST /api/tx/send: transports an already signed serialized transaction, not an authorization to spend server funds.

## Authorization
Wallet auth uses x-heisto-auth: publicKey.timestamp.signature. The signed message is exactly:
```text
Heisto auth
<wallet public key>
<UTC Unix timestamp in seconds>
```
The signature is Base58 Ed25519 and expires; timestamp validation is server-side. Never substitute a plain wallet address for a signature. Practice and private Guard key management require validated wallet authorization. /v1/guard uses Authorization: Bearer with a separately issued Guard key. Wallet signatures and Guard keys are not SOL transaction signatures or admin privileges.

Public listings/profile views are not private owner sessions. Routes that build unsigned transactions still rely on required on-chain signer constraints. Validate all returned transaction instructions before signing.

## Limits and errors
Pool and fee amounts are parsed as lamports, IDs remain strings/BigInt and the program enforces its constraints. Practice limits are UTC day based; Guard allowances are owner/month based across key changes. Rate limiting and quota consumption are separate controls. Errors must not silently return simulated balances, completions or verdicts. Provider failure does not establish settlement.
