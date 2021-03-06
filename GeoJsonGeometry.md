# GeoJSON feature geometries

Each regulation must be associated with a geographic feature, which must be a line segment (`LineString`). The geographic coordinates for the points that comprise this feature are contained within the `Feature` of a `Feature Class`. The coordinates should be based on the _matched SharedStreets output, not the input data_. This ensures that the resulting feature geometries have been snapped to the street and can be displayed on a map consistently.

(For a primer on GeoJSON terminology and structure, see [this post](https://macwright.org/2015/03/23/geojson-second-bite.html))

Each geographic coordinate should have no more than 7 decimal places of precision. This is sufficient to describe a location with ~1.1 cm accuracy. Further precision is unnecessary; less is sufficient.

Here's an example of the geometry of a GeoJSON feature. Note that the coordinates are for the signpost's location _after it was snapped to the street and extrapolated into a street segment_:

```json
{
  "type": "Feature",
  "geometry": {
    "type": "LineString",
    "coordinates": [
      [-112.12588548660278,33.45134313598914],
      [-112.12530076503754,33.45132075686167]
    ]
  }
}
```

# Examples

The links below show real world curb regulations translated into CurbLR.

| Link | Description |
| :---- | :---- |
| [Examples of simple regulations](examples/simple_examples.md) | Simple regulatory scenarios typically involving one or two basic restrictions  |
| [Examples of complex regulations](examples/complex_examples.md) | Complex regulatory scenarios typically involving several restrictions  |
| Large dataset of [Los Angeles' parking regulations, translated into CurbLR](/conversions/LA_CurbLR.json) | Contains data from 35,000 parking signs, many with multiple complex regulations. [Raw data](https://geohub.lacity.org/datasets/71c26db1ad614faab1047cc8c3686ece_28) was accessed through LA's open data portal, matched to the SharedStreets Referencing System, cleaned into a [CurbLR-ready CSV](/conversions/prepped_data.csv), and [converted](/js) into CurbLR's JSON format.
