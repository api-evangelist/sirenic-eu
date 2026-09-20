---
generated: '2026-09-19'
method: generated
name: Pay for a Sirenic call with x402 (or an API key) and verify the response
description: 'The access contract every other skill depends on: get the quote, sign it, retry, verify the signature,
  read the provenance.'
api: openapi/sirenic-eu-openapi.yml
operations:
- getReperer
- getEntrepriseBySiren
- getDemoEntreprise
source: Grounded in the literal GET paths of openapi/sirenic-eu-openapi.yml (the provider spec carries NO operationIds;
  the ids above are assigned by overlays/sirenic-eu-openapi-overlay.yaml) and in llms.txt, conventions/, errors/
  and asyncapi/sirenic-eu-webhooks.yml. Prices are the x-price values in the spec on 2026-09-19.
---

# Pay for a Sirenic call with x402 (or an API key) and verify the response

The access contract every other skill depends on: get the quote, sign it, retry, verify the signature, read the provenance.

## Access
- No credential by default: x402 pay-per-call (quote → sign → retry) or `X-Api-Key: srn_live_…` with prepaid credits. See `authentication/sirenic-eu-authentication.yml` and the skill `sirenic-eu-pay-per-call-x402.md`.
- All routes are `GET`; any other method is `405`. Non-2xx is never charged.

## Steps
1. **Rehearse for free** — `getDemoEntreprise` (`GET /v1/demo/entreprise`) `?siren=552032534` returns the real, signed profile response for two fixed SIREN; `getReperer` (`GET /v1/reperer`) `?texte=` extracts identifiers from pasted text and names the recommended call WITH its price.
2. **Quote** — call the paid route, e.g. `getEntrepriseBySiren` (`GET /v1/entreprise/{siren}`) ($0.005), with no payment: `402` with the x402 v2 quote in the body and the `PAYMENT-REQUIRED` header (`scheme exact`, `network eip155:8453`, USDC `0x8335…2913` or EURC `0x60a3…db42`, `payTo 0x76A6…C8A2`, `maxTimeoutSeconds 120`). Nothing is charged.
3. **Pay** — sign with an x402 client (`@x402/fetch`) and retry with `PAYMENT-SIGNATURE`. Default client cap is $1.00 per payment; only full-size `/v1/kyb/batch`, `/v1/surveillance/creer` and `…/renouveler` exceed it. EURC needs an explicit `spendControls.allowedAssets` opt-in. Or skip the wallet: `X-Api-Key: srn_live_…` (prepaid credits, 1 credit = 1 EUR; `X-Credits-Charged` / `X-Credits-Remaining` come back).
4. **Only 2xx is charged** — 400/402/404/5xx cancel the payment before settlement; 405 for any method but GET. A 503 says `retry in a few seconds`; a 502 names the upstream register.
5. **Verify, then read** — every 2xx `/v1` body carries a detached Ed25519 signature (`X-Sirenic-Signature`; message `sirenic-v1:<kid>:<timestamp>:<base64 sha256(raw bytes)>`, key at `/.well-known/sirenic-signing-key`) and a `provenance[]` array (source register, licence, `as_of`, `precision_as_of`, `etat`). Keep both: they let you prove later exactly what you knew when you paid.

## Errors
- `{error, champ, message}` on 400; `402` carries the quote (or `credits_insuffisants` on the key rail); `404` no diffusible company; `503` source down, retry. Full catalog: `errors/sirenic-eu-problem-types.yml`.

## Notes
- Officers are exposed as name, role and birth year only; partial-diffusion companies return a minimal record. Do not store or republish personal data beyond the task.
- Route names and fields are French; descriptions are bilingual. Reading rules: `GET /v1/lecture` (free).
