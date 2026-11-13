# Security readiness and evidence

Last reviewed: **2026-11-13T07:54:53.331Z** (UTC).
This page distinguishes observed evidence from planned work. It is not an audit.

## Status

| Item | Status at review | Evidence or completion criterion |
| --- | --- | --- |
| Mainnet receipts and recorded bytecode comparison | Historical evidence published | [Timestamped proof repository](https://github.com/heisto-dev/heisto-mainnet-proof); re-check current chain state before relying on it |
| Independent reproducible verified build | Not established in this review | Rebuild an exact public commit with pinned toolchain, compare deployed bytes and publish independently checkable verification |
| Website security.txt | Missing at review: HTTP 404 | Serve a valid plain-text document at the canonical HTTPS well-known path |
| Squads multisig upgrade authority | Not established in this review | Verify the actual ProgramData authority and publish the multisig address, members, threshold and authority-transfer receipt |
| Repository security policies | Present in all five official repositories | Private reports to support@heisto.xyz; [policy](SECURITY.md) |
| Public Dune dashboard | Not established in this review | Publish reproducible queries, program filters, freshness and dashboard URL |
| Hugging Face Guard Checker | Public release available | [Space](https://huggingface.co/spaces/heisto/guard-checker), [source](https://huggingface.co/spaces/heisto/guard-checker/tree/main) |
| Community listings | Submission is not acceptance | Maintainer review is required; a listing is not an audit or endorsement |

## Recommended protocol-assurance sequence

1. Establish an independently reproducible source-to-deployed-bytecode build,
   and publish a discoverable security contact.
2. Review migration to a Squads multisig with separately controlled signers.
3. Maintain source, build instructions, security policies and trust disclosures.
4. Publish a read-only Dune dashboard with clearly defined metrics.
5. Maintain the public Guard Checker and its limitations.
6. Submit evidence-backed directory entries without implying endorsement.

The checker has already shipped. Its narrowly scoped community submission
describes only the available prompt-inspection tool, not completion of the
protocol-assurance sequence above.

## Verified build is not an audit

A verified build demonstrates that a specific source revision and build
procedure reproduce the deployed program bytes. It does not show that the
program is bug-free, its economics are safe, the AI judges are correct, or
upgrade authority cannot change the program later.

A matching local binary hash alone is not an independently reproducible source
build. Record the source commit, toolchain and build inputs, deployed program
address, ProgramData slot, comparison procedure and verifier output.
Re-check after any upgrade.

## security.txt publication requirements

Publish at `https://heisto.xyz/.well-known/security.txt` as
`text/plain; charset=utf-8`. Include `Contact: mailto:support@heisto.xyz`,
a future UTC `Expires` value, `Canonical` for the same HTTPS URL,
`Preferred-Languages: en`, and a `Policy` link to this repository's SECURITY.md.
Choose and maintain a real expiry date; do not publish a placeholder.
Check the live response after release. A file in a repository alone does not
make the website endpoint available or prove the mailbox is monitored.

## Authority changes require a separate approval

No authority transfer, signing operation, program upgrade, wallet funding or
SOL spending is part of this documentation or community submission. Before
any multisig transfer, confirm independent signer custody, threshold, recovery
procedure, destination vault authority and the full transaction details.

## Dune evidence requirements

Distinguish attack fees, prize deposits, prize payouts and account rent.
Do not count a deposit as a successful payout. Explain decoded instructions,
excluded failed transactions, refresh times and historical coverage.

## Public wording

Use: "The Guard Checker is available for testing known prompt-injection
patterns. It is a first filter, not a full defense."

Do not say "audited", "immutable", "verified source build", "multisig secured",
"guaranteed safe" or "listed" unless the specific claim has current evidence.
An open pull request means submitted, not accepted.
