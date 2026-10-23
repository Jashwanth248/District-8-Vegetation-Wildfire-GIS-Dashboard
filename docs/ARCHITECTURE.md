# Architecture and GIS workflow

## Demo flow

1. `index.html` creates an in-memory set of fictional work orders and exposure overlays.
2. Leaflet renders map layers, schematic corridors, point popups, and map navigation.
3. Filters constrain the displayed features and work queue.
4. The browser timer adds a synthetic record or updates a synthetic status every 3.6 seconds.
5. Summary values, the priority queue, the activity feed, and the chart respond to those changes.
6. The export action serializes the filtered point records as GeoJSON using longitude/latitude coordinates.

## Coordinate reference and interchange

The demo stores coordinates as latitude/longitude decimal degrees and exports GeoJSON coordinates in `[longitude, latitude]` order using OGC CRS84 / WGS 84. Leaflet handles display projection for the basemap. The schematic corridor polylines and illustrative exposure circles are not authoritative spatial datasets.

## Production adaptation path

This prototype shows a front-end workflow. A production system would require decisions and controls outside the scope of a portfolio demo:

- Connect approved work activity feeds and authoritative transportation, vegetation, and wildfire datasets.
- Establish a documented schema, stable identifiers, coordinate reference systems, required metadata, and validation rules.
- Separate public, internal, and sensitive fields; apply authentication and role-based access before exposing restricted data.
- Replace the local timer with a supported event service or scheduled refresh process and expose data freshness and failure states.
- Publish governed feature services through the agency's approved ArcGIS Enterprise or ArcGIS Online environment.
- Validate spatial analyses, thresholds, cartographic conventions, reporting periods, and outputs with program data stewards.
- Add server-side logging, monitoring, audit trails, automated quality checks, and a deployment pipeline.

The demonstration intentionally does not make fire behavior predictions, assign real-world risk, or recommend field actions.
