# District 8 Vegetation & Wildfire GIS Dashboard

An interactive GIS operations dashboard concept for vegetation maintenance and wildfire readiness in Caltrans District 8. It combines a district-scale map, maintenance work queue, exposure overlays, activity indicators, and a browser-based event stream.

> **Demonstration only:** every work order, location, treatment area, exposure polygon, event, and activity metric in this project is synthetic or schematic. This application is not connected to Caltrans, IMMS, ArcGIS Enterprise, or any agency system. It must not be used for operational decisions.

## Preview

The dashboard opens to a District 8 map with schematic major corridors, synthetic maintenance points, and illustrative exposure areas. New simulated events arrive in the browser about every 3.6 seconds. Use **Pause stream** to stop them. Map filters update the visible work locations and priority queue. **Export data** downloads the visible work locations as GeoJSON in WGS 84.

## Features

- Interactive Leaflet map with corridor, work-order, and exposure layers.
- Filters for activity type and work status.
- Summary cards for work orders, treated acres, high-priority corridors, completion, and session events.
- Priority queue that flies the map to a selected work location.
- Live activity feed and rolling work-order trend.
- Pause/resume controls for the simulated event stream.
- GeoJSON export of the currently visible synthetic work orders.
- Responsive layout for desktop, tablet, and mobile screens.
- No API key, database, package installation, or build step required.

## Run locally

The app uses Leaflet, Chart.js, and a CARTO basemap loaded from public CDNs, so an internet connection is needed for the map and chart libraries.

```bash
git clone https://github.com/Jashwanth248/District-8-Vegetation-Wildfire-GIS-Dashboard.git
cd District-8-Vegetation-Wildfire-GIS-Dashboard
python3 -m http.server 8000
```

Open <http://localhost:8000> in a browser. You can also open `index.html` directly, but a local web server is more reliable.

## Technology

| Layer | Technology | Purpose |
|---|---|---|
| Web application | HTML, CSS, JavaScript | Self-contained responsive dashboard |
| Web mapping | Leaflet 1.9 | Interactive map, layers, popups, and map navigation |
| Basemap | CARTO light tiles | Public reference backdrop with OpenStreetMap attribution |
| Trend chart | Chart.js 4 | Rolling activity visualization |
| Event stream | Browser JavaScript timer | Reproducible-by-inspection synthetic event simulation |
| Interchange | GeoJSON, CRS84 / WGS 84 | Export visible work-order points for GIS tools |

## Architecture

```text
Synthetic work-order records ──┬──> Leaflet map and filters
                                ├──> KPI cards and priority queue
Synthetic event timer ─────────┼──> Activity feed and rolling trend
                                └──> GeoJSON export
```

All application logic is in `index.html`. The demo is intentionally dependency-light: third-party browser libraries and basemap tiles are loaded from CDNs, while work-order data is generated in the browser and is not sent to a service.

## Data and interpretation

- **Work records:** generated randomly in the browser with fictional IDs, work types, locations, statuses, acre estimates, and priorities.
- **Live updates:** the timer creates new fictional work orders and changes synthetic statuses. The “live” label refers only to this local simulation.
- **Corridors:** hand-drawn schematic lines for orientation. They are not engineering alignments or authoritative Caltrans centerlines.
- **Exposure areas:** illustrative circles with synthetic acreage values. They are not mapped fuels, fire perimeters, or official risk assessments.
- **Metrics:** computed from the in-memory demo records. They are not program performance measures.
- **Export:** GeoJSON includes a `data_classification` property on each feature to retain the synthetic-data label.

See [`docs/DATA_DICTIONARY.md`](docs/DATA_DICTIONARY.md) for fields and [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) for the design and production adaptation path.

## GIS handoff

Use **Export data** to download `district-8-vegetation-work.geojson`. The file can be opened in QGIS or ArcGIS Pro and transformed to GeoPackage, Shapefile, or a hosted feature layer. This demo does not publish data to ArcGIS Online or Enterprise. A production implementation would need approved source systems, access controls, data governance, and validation with the program owner before publishing.

## Accessibility and browser notes

The dashboard uses semantic page sections, labeled filters, keyboard-accessible buttons, and responsive layouts. Map interactions are provided by Leaflet; users who cannot use a map can use the priority queue and exported GeoJSON. Current Chrome, Firefox, Safari, or Edge is recommended.

## License

This portfolio demo is provided under the MIT License. See [`LICENSE`](LICENSE).
