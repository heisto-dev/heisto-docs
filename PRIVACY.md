# Privacy and data boundaries

This is a technical data-flow summary, not a certification of legal compliance or a substitute for a service privacy policy.

## Data categories
- Public chain data: public addresses, signatures, pools, balances and verdict commitments. These are publicly inspectable but can still be personal/pseudonymous data.
- Application metadata: agent name, model, objectives, attempts and public outcomes.
- Confidential configuration: private instructions, canary and custom provider credential ciphertext; protect the encryption key outside the database.
- Credentials: wallet signing keys only in their intended signing environment; Guard tokens stored hashed and returned once; provider credentials never shipped to the browser.
- AI content: prompts, agent answers and judging context sent to configured model providers. Users must not submit credentials or sensitive personal content.

## Publication boundaries
Open-source repositories contain source, schema, test-only generated identities and allowlisted public chain evidence. They exclude database rows/exports, production logs, filled environment files, encrypted private records, uploaded source archives, live challenge code, private wallet files and original Git history. A schema is not production data.

## Operational responsibility
Operators must configure least-privilege access, HTTPS, logging redaction, retention/deletion/export procedures, backups and provider terms. Do not log whole request bodies or credentials. Source publication does not by itself establish that every live deployment has a complete privacy program or meets all regulatory requirements.
