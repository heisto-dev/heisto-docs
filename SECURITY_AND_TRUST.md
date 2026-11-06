# Security, economics and limitations

## Threats and controls
| Risk | Boundary/control | Remaining limitation |
| --- | --- | --- |
| Unauthorized wallet spending | User-signed transaction; program signers/seeds; quote max_fee | Users must inspect prepared transactions; UI compromise remains dangerous |
| Forged/replayed verdict | Ed25519 verification and Sentinel/Attack/sequence/outcome/score/response binding | Configured signer is a trusted authority |
| Prompt injection | Bounded prompts, separated instructions, explicit jury criteria | Model compliance is not guaranteed; never give it wallet tools |
| Private challenge disclosure | Encryption at rest; allowlisted outputs; confidential Practice judge reasons withheld | Model providers process confidential context; real breaches may occur |
| Key rotation quota reset | Persistent owner/month Guard accounting across revocation/rotation | Depends on database integrity and availability |
| Fake Mainnet claims | Receipt/account checks and real empty/unavailable states | A source release or UI badge alone does not prove payout |
| Program replacement | Public upgrade authority and bytecode verification | Contract remains upgradeable, not immutable |

## Economics
The current Config splits settled fees 50% pool, 35% defender, 10% treasury and 5% owner-held reserve including integer remainder. No automatic token burn is implemented. Before a breach payout, the pool share is added and the resulting pool is paid to the winner. Defender fees remain separate. Seven-day latest-funding lock and 24-hour post-deactivation delay both govern withdrawal. An eligible unsettled attack can be refunded after 15 minutes. Network fees are consumed.

## Current evidence boundary
The proof repository establishes an executable Mainnet program, matching recorded bytecode, finalized initialization/unpause and real Sentinel creation/funding. It does not establish an independent reproducible source build or audit. The first funded agent had no paid attack receipts at the published verification snapshot; a prize payout/refund must have its own evidence.

## Dependency review
The source audit recorded 0 critical/high dependency findings and 8 moderate entries across the broader reviewed dependency graph (including repeated advisories affecting one package). Relevant chains include Solana/Anchor serialization/cryptographic dependencies and stream-json through the JS chain stack. Counts are snapshot- and scanner-dependent; rerun pnpm audit and a current Rust advisory check. Static code review found no SAST findings in that scan. These results are not a security certification.

Operator scripts, runtime configuration and original history are not part of the allowlisted source export. Security scanning does not prove the absence of secrets or vulnerabilities; read the release scanning manifest and review changes before publishing.

Report privately: support@heisto.xyz. Do not put live exploit data or confidential values in public issues.
