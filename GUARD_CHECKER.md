# Heisto Guard Checker

**Guard is a first filter, not a full defense.**

- [Try the public Hugging Face Space](https://huggingface.co/spaces/heisto/guard-checker)
- [Inspect the MIT-licensed Space source](https://huggingface.co/spaces/heisto/guard-checker/tree/main)
- [Heisto application source](https://github.com/heisto-dev/heisto-app)
- Security reports: **support@heisto.xyz**

## Purpose and boundaries

Inspect non-sensitive text for known prompt-injection patterns before passing
it to an AI application. The static browser interface calls the public Heisto
Guard API. It is not a newly trained model, autonomous agent, wallet, trading
tool or security certification. It does not execute the submitted instructions.

## Try it

1. Open the Space and select an example, or paste non-sensitive text.
2. Press **Check**. Selecting an example does not send it.
3. Inspect the action, heuristic score, categories and raw JSON.
4. Compare harmless text with instruction-override attempts. Keep tool access,
   authorization and confidential data protected independently.

No visitor API key, wallet connection, transaction or prize deposit is needed.
The limit is 4,000 JavaScript string units. The public API has a limit of
30 requests per minute per IP per API process. A network error is not an ALLOW.

## API and interpretation

POST `https://heisto.xyz/api/guard/score` with JSON
`{"input":"text to inspect"}`. No Authorization header is sent.

The `heuristic-rules-v2` response exposes `score`, `action`, `categories`,
`owasp`, `method` and `warning`.

| Score | Action |
| --- | --- |
| Below 0.30 | ALLOW |
| 0.30 to below 0.60 | FLAG |
| 0.60 and above | BLOCK |

The score is not an attack probability. **ALLOW is not proof of safety.**
Pattern-based detection has false positives and missed attacks. Encoded
payloads and transcript tricks may evade it. BLOCK does not mean a downstream
application is automatically prevented from executing anything: enforcement
belongs to that application's own integration.

## Data handling

Submitted text leaves the browser for the public API over HTTPS. Do not submit
keys, passwords, personal data or confidential documents. The checker has no
browser storage or analytics and does not intentionally store submitted text.
Network and hosting providers may process operational metadata; no
zero-retention guarantee is made. Duplicated Spaces require their own reviewed
API-origin configuration, not a secret embedded in browser code.

## Separate trust claims

A hosted checker is not proof of a verified on-chain source build. Bytecode
comparison is not an independent audit. The Heisto program remains upgradeable
unless fresh on-chain evidence establishes otherwise.

See [security and trust](SECURITY_AND_TRUST.md) and
[security readiness](SECURITY_READINESS.md).
