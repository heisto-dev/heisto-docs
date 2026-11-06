# Create your Sentinel

1. Open https://heisto.xyz/#deploy and connect your intended owner wallet. Never enter a wallet secret into an agent field.
2. Choose an available model and a unique name. Claude is the model used by the verified Vault Keeper example.
3. Write public instructions (visible to attackers). Write private challenge rules using a new high-entropy test secret, never real credentials or personal information.
4. Define the Goal and a precise Jury prompt. For an exact-code challenge, set Exact secret to the same private challenge value. Attacker assertions and private judge reasoning should not count as an agent disclosure.
5. Set SOL pool and starting fee. Example: 0.5 SOL pool and 0.001 SOL fee. Current minimum 0.5 SOL, configured cap 2 SOL, starting fee positive and at most 1% of pool.
6. Review, select Deploy Sentinel and inspect the Mainnet transaction in your wallet. Check owner, program, amounts and full cost. Approve only inside your budget.
7. Wait for confirmation and verify the live page, Sentinel account and transaction. A draft is not a deployed/funded agent.

## Actual example
[Vault Keeper Mainnet](https://heisto.xyz/#sentinel-3544635135356959125) was funded with 0.5 SOL. Creation cost was 0.50152284 SOL: 0.5 prize + 0.00151384 account reserve + 0.000009 transaction fee. This is a historical example, not a fixed quote. [Receipt](https://explorer.solana.com/tx/4xTdmpzFAmGnePVp5MFXtWyX8BZRyaDV2ZiButF69cJtjK72bn1rS4zWpQ9f2ykEcQ8XAkYpALZ7ag6KHPjYVtkL).

Pool locks seven days since latest funding; withdrawal also requires at least 24 hours after deactivation. Successful attackers can win the pool. Do not fund with money you cannot risk.

If a signature exists but the UI fails, keep it and reconcile the existing creation instead of funding again. Contact support@heisto.xyz for support without sharing keys, confidential challenge values or personal data.
