---
name: load-a-bc-map-layer
description: >-
  Cross from a British Columbia Data Catalogue dataset record to the live DataBC OGC map
  service, and pull the layer as GeoJSON or as a rendered image.
api: british-columbia-data-catalogue:ckan-api
operations:
  - packageSearch
  - packageShow
  - resourceShow
base_url: https://catalogue.data.gov.bc.ca/api/3
ogc_endpoint: https://openmaps.gov.bc.ca/geo/pub/ows
auth: none
---

# Load a B.C. map layer

The catalogue holds the metadata; the geometry lives in the BC Geographic Warehouse and is
served by DataBC as OGC WMS 1.3.0 and WFS 2.0.0 — 895 layers and 896 feature types. This
skill is the join between the two.

## Steps

1. **Find geospatial records.** Call `packageSearch` with
   `q=res_format:wms` (884 datasets) or `q=res_extras_bcdc_type:geographic`, plus your
   topic terms.

2. **Open the record.** Call `packageShow` with the slug. Inside `resources[]`, find the
   entry whose `format` is `wms`. Two fields matter:
   - `url` — already a complete GetCapabilities URL for that single layer, e.g.
     `https://openmaps.gov.bc.ca/geo/pub/WHSE_LAND_AND_NATURAL_RESOURCE.PROT_CURRENT_FIRE_POLYS_SP/ows?service=WMS&request=GetCapabilities`
   - `object_name` — the BC Geographic Warehouse table name, e.g.
     `WHSE_LAND_AND_NATURAL_RESOURCE.PROT_CURRENT_FIRE_POLYS_SP`. **This is the layer name
     in the OGC services.** Use it verbatim; do not derive it from the dataset title.

3. **Pull features as GeoJSON** from the shared WFS endpoint:

   ```
   GET https://openmaps.gov.bc.ca/geo/pub/wfs
       ?service=WFS&version=2.0.0&request=GetFeature
       &typeName={object_name}
       &outputFormat=application/json
       &count=100
   ```

   Always set `count` — several of these layers are province-scale and unbounded requests
   are very large. Page with `startIndex`.

4. **Or render a map image** from WMS:

   ```
   GET https://openmaps.gov.bc.ca/geo/pub/ows
       ?service=WMS&version=1.3.0&request=GetMap
       &layers={object_name}&styles=
       &crs=EPSG:3005&bbox={miny},{minx},{maxy},{maxx}
       &width=800&height=600&format=image/png
   ```

   EPSG:3005 (BC Albers) is the provincial projection. Note the WMS 1.3.0 axis-order rule:
   for a geographic CRS the bbox is lat,lon — getting this backwards returns a blank image
   rather than an error.

5. **Check what a layer supports** before assuming. Fetch the per-layer GetCapabilities
   from the resource's own `url`; the saved province-wide capabilities documents in this
   repo (`openapi/british-columbia-data-catalogue-databc-pub-wms-capabilities.xml` and
   `...-wfs-capabilities.xml`) list every layer, its bounding box and its available
   formats.

## Available output formats

WMS `GetMap` advertises `image/png`, `application/json;type=geojson`,
`application/json;type=topojson`, `application/json;type=utfgrid`, `application/pdf`,
`application/rss+xml` and `application/vnd.google-earth.kml+xml`.

## Errors

- The OGC services return an `ows:ExceptionReport` XML document, **not** the CKAN
  envelope, and often with HTTP 200. Parse the body: a root of `ows:ExceptionReport` is a
  failure regardless of the status code.
- `WMTS`, `WCS` and `CSW` are not served here. Requesting them returns an
  `ows:ExceptionReport` or a 404.

## Cautions

- The catalogue and the map services are different hosts with different contracts. Do not
  send CKAN parameters to `openmaps.gov.bc.ca` or OGC parameters to the catalogue.
- Neither host publishes a rate limit or returns backoff headers. Throttle yourself.
