# British Columbia Data Catalogue

The British Columbia Data Catalogue is the official open data portal for the Government of British Columbia, Canada. Built on the CKAN open data platform, it provides programmatic access to thousands of BC government datasets covering demographics, environment, geospatial data, finance, transportation, and health.

## API Overview

The catalogue exposes a CKAN v3 REST API at:
```
https://catalogue.data.gov.bc.ca/api/3/action/
```

No authentication required for read access to public datasets. All responses return JSON with `help`, `success`, and `result` fields.

## Key Endpoints

| Endpoint | Description |
|----------|-------------|
| `package_list` | List all available dataset identifiers |
| `package_search?q={query}` | Search datasets by keyword or filter |
| `package_show?id={id}` | Retrieve metadata and resources for a specific dataset |
| `organization_list` | List BC government organizations publishing data |
| `resource_show?id={id}` | Retrieve information about a specific data resource |

## Example Request

```bash
curl "https://catalogue.data.gov.bc.ca/api/3/action/package_search?q=census"
```

## Data Categories

- Census and demographic data
- Environmental and climate information
- Geographic and mapping datasets
- Financial and economic reports
- Transportation and infrastructure data
- Health and social services statistics
- Natural resources and land use

## Links

- [Data Catalogue](https://catalogue.data.gov.bc.ca/)
- [API Base URL](https://catalogue.data.gov.bc.ca/api/3/action/)
- [Dataset List](https://catalogue.data.gov.bc.ca/api/3/action/package_list)
- [BC Government Data Portal](https://www2.gov.bc.ca/gov/content/data/bc-data-catalogue)
