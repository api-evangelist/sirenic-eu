---
generated: '2026-09-19'
method: generated
name: Verify a French or European supplier before paying an invoice
description: Resolve the supplier to its identifier, then get the invoicing verdict (identity + VAT live against
  VIES + IBAN form check + ready-to-invoice verdict) in one paid call.
api: openapi/sirenic-eu-openapi.yml
operations:
- getSuggestions
- getRecherche
- getFacturationDossier
- getEuFacturationDossier
- getTvaVerifierByNumero
- getIbanVerifierByIban
source: Grounded in the literal GET paths of openapi/sirenic-eu-openapi.yml (the provider spec carries NO operationIds;
  the ids above are assigned by overlays/sirenic-eu-openapi-overlay.yaml) and in llms.txt, conventions/, errors/
  and asyncapi/sirenic-eu-webhooks.yml. Prices are the x-price values in the spec on 2026-09-19.
---

# Verify a French or European supplier before paying an invoice

Resolve the supplier to its identifier, then get the invoicing verdict (identity + VAT live against VIES + IBAN form check + ready-to-invoice verdict) in one paid call.

## Access
- No credential by default: x402 pay-per-call (quote → sign → retry) or `X-Api-Key: srn_live_…` with prepaid credits. See `authentication/sirenic-eu-authentication.yml` and the skill `sirenic-eu-pay-per-call-x402.md`.
- All routes are `GET`; any other method is `405`. Non-2xx is never charged.

## Steps
1. **Resolve the name (free)** — `getSuggestions` (`GET /v1/suggestions`) `?q=<name>` returns up to 5 SIREN candidates. If you already hold a SIREN, SIRET or FR VAT number, paste it as-is into `getRecherche` (`GET /v1/recherche`) `?q=` ($0.002) — spacing and labels are stripped server-side.
2. **France: one call** — `getFacturationDossier` (`GET /v1/facturation/dossier`) `?siren=&iban=` ($0.03). Read `verdict.pret_a_facturer` AND `verdict.non_verifie[]` and `verdict.raisons[]` (closed list, each `bloquante` or `information`). `tva_non_verifiable` means VIES was down — it is informational, never a false invalid.
3. **Belgium / Poland** — `getEuFacturationDossier` (`GET /v1/eu/facturation/dossier`) `?pays=BE|PL&id=&iban=` ($0.03); Poland adds whether the IBAN is declared in the White List (paying >15,000 PLN to an undeclared account costs the buyer the VAT deduction).
4. **Pieces on their own** — `getTvaVerifierByNumero` (`GET /v1/tva/verifier/{numero}`) ($0.003) and `getIbanVerifierByIban` (`GET /v1/iban/verifier/{iban}`) ($0.005).
5. **Say what was NOT checked** — Sirenic never verifies the account holder's name or the account's existence, and is not an accredited e-invoicing platform (PDP/PA); `verification_titulaire: non_disponible` travels in every IBAN payload. Report it next to the green light.

## Errors
- `{error, champ, message}` on 400; `402` carries the quote (or `credits_insuffisants` on the key rail); `404` no diffusible company; `503` source down, retry. Full catalog: `errors/sirenic-eu-problem-types.yml`.

## Notes
- Officers are exposed as name, role and birth year only; partial-diffusion companies return a minimal record. Do not store or republish personal data beyond the task.
- Route names and fields are French; descriptions are bilingual. Reading rules: `GET /v1/lecture` (free).
