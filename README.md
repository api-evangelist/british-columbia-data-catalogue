# British Columbia Data Catalogue (british-columbia-data-catalogue)

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
