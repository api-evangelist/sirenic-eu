---
generated: '2026-09-19'
method: generated
name: Build a KYB decision file for a French company
description: One call returns identity, officers, BODACC alerts, filed accounts, sanctions screening of company
  and officers, and the computed VAT number — with per-block provenance.
api: openapi/sirenic-eu-openapi.yml
operations:
- getRecherche
- getKybBySiren
- getEntrepriseBySirenDossier
- getKybBatch
- getSanctionsCheck
- getScoreDefaillanceBySiren
source: Grounded in the literal GET paths of openapi/sirenic-eu-openapi.yml (the provider spec carries NO operationIds;
  the ids above are assigned by overlays/sirenic-eu-openapi-overlay.yaml) and in llms.txt, conventions/, errors/
  and asyncapi/sirenic-eu-webhooks.yml. Prices are the x-price values in the spec on 2026-09-19.
---

# Build a KYB decision file for a French company

One call returns identity, officers, BODACC alerts, filed accounts, sanctions screening of company and officers, and the computed VAT number — with per-block provenance.

## Access
- No credential by default: x402 pay-per-call (quote → sign → retry) or `X-Api-Key: srn_live_…` with prepaid credits. See `authentication/sirenic-eu-authentication.yml` and the skill `sirenic-eu-pay-per-call-x402.md`.
- All routes are `GET`; any other method is `405`. Non-2xx is never charged.

## Steps
1. **Resolve** — `getRecherche` (`GET /v1/recherche`) `?q=` ($0.002); use `score_confiance` to disambiguate homonyms and stop if `aucune_correspondance_fiable` is true.
2. **Full file** — `getKybBySiren` (`GET /v1/kyb/{siren}`) ($0.15). For a portfolio, `getKybBatch` (`GET /v1/kyb/batch`) `?sirens=a,b,c` (2-100 SIREN, $0.105 each; unknown SIREN come back `trouve: false` and are billed as one lookup). The full-size quote can exceed the $1.00 default x402 client cap — raise `spendControls.maxAmountPerPayment` first.
3. **Pay only for the blocks you read** — `getEntrepriseBySirenDossier` (`GET /v1/entreprise/{siren}/dossier`) `?blocs=finances,score,alertes_bodacc` ($0.005 + each block's own price, capped $0.35). Unserved blocks are NAMED in `blocs_absents` with `aucune_donnee` | `non_diffusible` | `panne_amont`.
4. **Risk and sanctions separately** — `getScoreDefaillanceBySiren` (`GET /v1/score/defaillance/{siren}`) (0-100 at ~12 months, each component with threshold and confidence) and `getSanctionsCheck` (`GET /v1/sanctions/check`) `?nom=` ($0.02, 6 official lists, each dated in `listes_consultees`).
5. **Read the states before the numbers** — every block carries `provenance[].etat`: only `absence_mesuree` asserts an absence; `absence_non_conclusive`, `partiel`, `indisponible` are not 'nothing to report'. A sanctions match is a name match to verify, never a decision. Dictionaries are free at `GET /v1/lecture` and `GET /v1/provenance/registres`.

## Errors
- `{error, champ, message}` on 400; `402` carries the quote (or `credits_insuffisants` on the key rail); `404` no diffusible company; `503` source down, retry. Full catalog: `errors/sirenic-eu-problem-types.yml`.

## Notes
- Officers are exposed as name, role and birth year only; partial-diffusion companies return a minimal record. Do not store or republish personal data beyond the task.
- Route names and fields are French; descriptions are bilingual. Reading rules: `GET /v1/lecture` (free).
