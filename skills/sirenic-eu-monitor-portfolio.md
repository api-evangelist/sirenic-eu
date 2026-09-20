---
generated: '2026-09-19'
method: generated
name: Monitor a customer or supplier portfolio for legal events
description: Register up to 100 targets for daily checks against BODACC, Sirene, sanctions, AMF, Seveso and procurement
  sources, delivered by Ed25519-signed webhook, e-mail digest or pull.
api: openapi/sirenic-eu-openapi.yml
operations:
- getSurveillanceCreer
- getSurveillanceByJeton
- getSurveillanceByJetonRenouveler
- getSurveillanceByJetonArreter
- getEntrepriseBySirenChangements
source: Grounded in the literal GET paths of openapi/sirenic-eu-openapi.yml (the provider spec carries NO operationIds;
  the ids above are assigned by overlays/sirenic-eu-openapi-overlay.yaml) and in llms.txt, conventions/, errors/
  and asyncapi/sirenic-eu-webhooks.yml. Prices are the x-price values in the spec on 2026-09-19.
---

# Monitor a customer or supplier portfolio for legal events

Register up to 100 targets for daily checks against BODACC, Sirene, sanctions, AMF, Seveso and procurement sources, delivered by Ed25519-signed webhook, e-mail digest or pull.

## Access
- No credential by default: x402 pay-per-call (quote → sign → retry) or `X-Api-Key: srn_live_…` with prepaid credits. See `authentication/sirenic-eu-authentication.yml` and the skill `sirenic-eu-pay-per-call-x402.md`.
- All routes are `GET`; any other method is `405`. Non-2xx is never charged.

## Steps
1. **This is a WRITE that spends money and cannot be refunded** — `getSurveillanceCreer` (`GET /v1/surveillance/creer`) `?cibles=<SIREN,RNA,dirigeant:Name>&duree=30|90|365&webhook=&email=` ($0.05 / $0.135 / $0.50 per target). Get the quote first (call without payment), confirm the amount with the user, and do not retry blindly after a network failure: there is no Idempotency-Key, a second signed call creates a second watch.
2. **Keep the token** — the response returns the same bearer capability as `jeton` and `surveillance_id` (`sw_<uuid>.<timestamp>.<sig>`). Whoever holds it can read and stop the watch.
3. **Read events** — `getSurveillanceByJeton` (`GET /v1/surveillance/{jeton}`) (free): status `active | expiree_renouvelable | expiree`, targets with last-checked timestamps, the last 100 events with delivery status. Webhook batches carry `X-Sirenic-Signature`; verify Ed25519 over `sirenic-v1:<kid>:<timestamp>:<base64 sha256(raw body)>` with the key from `/.well-known/sirenic-signing-key`, allowing a few minutes of clock tolerance (retries reuse the original timestamp for ~33 s; next-day redelivery gets a fresh one).
4. **Renew or stop** — `getSurveillanceByJetonRenouveler` (`GET /v1/surveillance/{jeton}/renouveler`) `?duree=` (paid; 410 once the post-expiry grace period has passed); `getSurveillanceByJetonArreter` (`GET /v1/surveillance/{jeton}/arreter`) stops and purges immediately, free. An `expiration_proche` event fires 7 days before expiry on every channel.
5. **Polling alternative without a watch** — `getEntrepriseBySirenChangements` (`GET /v1/entreprise/{siren}/changements`) `?depuis=YYYY-MM-DD` ($0.01) returns new BODACC announcements since a date.

## Errors
- `{error, champ, message}` on 400; `402` carries the quote (or `credits_insuffisants` on the key rail); `404` no diffusible company; `503` source down, retry. Full catalog: `errors/sirenic-eu-problem-types.yml`.

## Notes
- Officers are exposed as name, role and birth year only; partial-diffusion companies return a minimal record. Do not store or republish personal data beyond the task.
- Route names and fields are French; descriptions are bilingual. Reading rules: `GET /v1/lecture` (free).
