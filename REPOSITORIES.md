# Repository map and evidence verification

- [heisto-app](https://github.com/heisto-dev/heisto-app)
- [heisto-contracts](https://github.com/heisto-dev/heisto-contracts)
- [heisto-sdk](https://github.com/heisto-dev/heisto-sdk)
- [heisto-docs](https://github.com/heisto-dev/heisto-docs)
- [heisto-mainnet-proof](https://github.com/heisto-dev/heisto-mainnet-proof)

heisto-app is the original UI/API source; heisto-contracts is the Anchor program; heisto-sdk is the actual binary client; heisto-docs explains behavior; heisto-mainnet-proof publishes timestamped public receipts and a read-only verification script.

Use the evidence repository to compare Mainnet genesis, loader, executable flag, ProgramData address, authority, exact program payload hash and creation receipt. A hash match to the recorded binary is narrower than independent source-to-binary verification. Do not infer 100% end-to-end reliability or security from funding evidence.

Each repository has MIT licensing, security/contact/contribution guidance and a clean initial history. Publication review rejects sensitive filenames, known live credential values, credential-like literals and host-specific/internal configuration. Existing third-party licenses and trademarks remain applicable.
