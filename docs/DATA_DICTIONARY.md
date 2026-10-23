# Data dictionary

All records described here are generated synthetic demonstration data. The field names are illustrative and are not an official Caltrans data contract.

## Work-order point properties

| Field | Type | Meaning |
|---|---|---|
| `work_order_id` | string | Fictional identifier such as `VM-58231`. |
| `activity_type` | string | Fictional vegetation activity category. |
| `status` | string | `In progress`, `Queued`, or `Complete`. |
| `priority` | string | Demo priority label derived from the synthetic risk class. |
| `risk` | string | `High`, `Moderate`, or `Standard` demo classification. |
| `corridor` | string | Fictional or illustrative route reference. |
| `community` | string | Generalized nearby community label. |
| `site` | string | Fictional site name. |
| `acres_treated` | number | Synthetic estimated treatment acreage. |
| `last_updated` | ISO 8601 datetime | Browser-generated update timestamp. |
| `data_classification` | string | Always `Synthetic demonstration data` in the export. |

## Geometry

Export features are GeoJSON `Point` geometries. Coordinates are `[longitude, latitude]` in decimal degrees (WGS 84 / CRS84). No exported point represents a verified maintenance work location.
