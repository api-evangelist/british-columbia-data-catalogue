---
name: find-a-bc-dataset
description: >-
  Search the British Columbia Data Catalogue for datasets matching a topic, publisher or
  file format, and return the download or service URLs for the best matches.
api: british-columbia-data-catalogue:ckan-api
operations:
  - packageSearch
  - packageShow
  - organizationList
base_url: https://catalogue.data.gov.bc.ca/api/3
auth: none
---

# Find a B.C. dataset

The catalogue holds 3,356 dataset records from 244 Government of British Columbia
organizations. Reads need no key and no account.

## Steps

1. **Search.** Call `packageSearch` — `GET /action/package_search?q={query}&rows=20`.
   `q` is a Solr query string, not plain keyword search. Plain words work, but field
   queries are far more precise:
   - `q=res_format:csv` — datasets with a CSV distribution
   - `q=res_format:wms` — datasets with a live map service (884 of them)
   - `q=res_extras_bcdc_type:geographic` — geospatial records
   - `q=license_id:2` — records under a specific licence
   Combine with `fq` for filters, and `facet=true&facet.field=["organization"]` to see
   which ministries publish in the space before narrowing.

2. **Read the envelope, not the status code.** A CKAN response is
   `{help, success, result}`. Check `success` first. On the search response,
   `result.count` is the total match count and `result.results` is the page.

3. **Page.** `package_search` uses `rows` (page size) and `start` (offset) — not
   `limit`/`offset`, which is what the plain list actions use. Advance `start` by `rows`
   until `start >= result.count`.

4. **Open a record.** Call `packageShow` — `GET /action/package_show?id={name}`, where
   `name` is the slug from the search hit (`result.results[].name`), not the title.
   The response carries `resources[]`, which is where the actual data lives.

5. **Pick the right distribution.** Each resource has `format` (csv, wms, kml,
   arcgis_rest, shp, oracle_sde) and `url`. Prefer `csv` or `application/json` for
   tabular work; prefer `wms`/`wfs` for anything mapped. A `format: multiple` resource
   with an empty `url` is a grouping placeholder — skip it.

6. **Identify the publisher when you need to.** `packageShow` embeds `organization`;
   `organizationList` enumerates all 244 if you need to browse by ministry.

## Errors

- **404 `Not Found Error`** — the `id` is not a real dataset slug. Re-run `packageSearch`;
  do not guess slugs from titles.
- **409 `Validation Error`** — a required parameter is missing. The failing field names are
  keys under `error`, each holding an array of messages. There is no `error.message` on
  this shape.
- **400, bare JSON string** — the action name is wrong or you used GET on a write action.
  The body is a string, not an object; parsing for `.error` yields undefined.

## Cautions

- No rate limits are published and no `RateLimit-*` or `Retry-After` headers are returned.
  Back off on your own schedule — you will get no runtime warning before being cut off.
- `q` is Solr syntax. Unescaped colons, quotes and spaces in a user-supplied string will
  produce a silently wrong result set rather than an error. URL-encode, and quote
  multi-word field values.
- Do not call `user_list`. It answers anonymously and returns names of B.C. public
  servants; it has no place in a dataset search.
