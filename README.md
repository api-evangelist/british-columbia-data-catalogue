# British Columbia Data Catalogue (british-columbia-data-catalogue)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

The British Columbia Data Catalogue is the official open data portal for the Government of British Columbia, Canada. Built on the CKAN open data platform, it provides programmatic access to thousands of BC government datasets spanning census and demographic data, environmental and climate information, geospatial and mapping data, financial reports, transportation and infrastructure data, and health and social services statistics. The CKAN API at api/3/action/ enables searching, listing, and retrieving dataset metadata and resources without authentication.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/british-columbia-data-catalogue/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/british-columbia-data-catalogue/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** Open

## Tags

- Open Data
- Government
- Canadian Government
- British Columbia
- Provincial Data
- CKAN
- Geospatial

## Timestamps

- **Created:** 2024-11-07
- **Modified:** 2026-04-21

## APIs

### BC Data Catalogue CKAN API

The BC Data Catalogue exposes a CKAN v3 REST API at https://catalogue.data.gov.bc.ca/api/3/action/ providing programmatic access to BC government open datasets. Key endpoints include package_list (list all datasets), package_search (search datasets by query), package_show (retrieve dataset metadata and resources), organization_list (list BC government organizations), and resource_show (retrieve specific data resource information). Returns JSON with success status and result payloads. No authentication required for read access to public datasets.

- **Human URL:** [https://catalogue.data.gov.bc.ca/](https://catalogue.data.gov.bc.ca/)

#### Tags

- CKAN
- Open Data
- Dataset Search
- Metadata
- Government Data

#### Properties

- [Documentation](https://catalogue.data.gov.bc.ca/)
- [Base U R L](https://catalogue.data.gov.bc.ca/api/3)
- [Postman Collection](collections/british-columbia-data-catalogue.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/british-columbia-data-catalogue.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Website](https://catalogue.data.gov.bc.ca/)
- [A P I Base U R L](https://catalogue.data.gov.bc.ca/api/3/action/)
- [Dataset List](https://catalogue.data.gov.bc.ca/api/3/action/package_list)
- [Dataset Search](https://catalogue.data.gov.bc.ca/api/3/action/package_search)
- [Government Portal](https://www2.gov.bc.ca/gov/content/data/bc-data-catalogue)
- [L L Ms Txt](https://catalogue.data.gov.bc.ca/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
