# RoadEventFeature Object (GeoJSON Feature)
The `RoadEventFeature` object is the container object for a TDx road event [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md), [DetourRoadEvent](/spec-content/objects/DetourRoadEvent.md) or [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md). The `RoadEventFeature` object is an instance of a [GeoJSON Feature](https://tools.ietf.org/html/rfc7946#section-3.2).

This object was initially developed for the [WZDx Specification](https://github.com/usdot-jpo-ode/wzdx).

## Properties
Name | Type | Description | Conformance | Notes
--- | --- | --- | --- | ---
`id` | String | A unique identifier issued by the data feed provider to identify the TDx road event. It is recommended that this identifier is a Universally Unique IDentifier (UUID) as defined in [RFC 4122](https://datatracker.ietf.org/doc/html/rfc4122) to guarantee uniqueness between feeds and over time. | Required | This is a GeoJSON property. 
`type` | String; `"Feature"` | The GeoJSON object type. This MUST be the string `Feature`. | Required | This is a GeoJSON property.
`properties` | One of: [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md), [DetourRoadEvent](/spec-content/objects/DetourRoadEvent.md),  [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md) | The specific details of the road event. | Required | This is a GeoJSON property.
`geometry` | GeoJSON [Geometry](https://tools.ietf.org/html/rfc7946#section-3.1) object with `type` of [LineString](https://tools.ietf.org/html/rfc7946#section-3.1.4) or [MultiPoint](https://tools.ietf.org/html/rfc7946#section-3.1.3) | The geometry of the road event. The Geometry object's `type` property MUST be [LineString](https://tools.ietf.org/html/rfc7946#section-3.1.4) or [MultiPoint](https://tools.ietf.org/html/rfc7946#section-3.1.3). `LineString` allows specifying the entire road event path and should be preferred. `MultiPoint` should be used when only the start and end coordinates are known. The order of coordinates is meaningful: the first coordinate is the first (furthest upstream) point a road user encounters when traveling through the road event. If a data producer has three or more coordinates that are on the road event path, a `LineString` geometry should be used because it indicates that the points are ordered. | Required | Feed producers should aim to provide a higher density of points for sections of roadways with curves so that data consumers can more easily match road events to their road network. This is a GeoJSON property.
`bbox` | GeoJSON [Bounding Box](https://tools.ietf.org/html/rfc7946#section-5) | Information on the coordinate range for this RoadEventFeature. Must be an array of length `2n` where `n` is the number of dimensions represented in the `geometry` property, with all axes of the most southwesterly point followed by all axes of the more northeasterly point.  The axes order of a bbox follows the axes order of the `geometry`. | Optional | This is a GeoJSON property.

## Used By
Property | Object
--- | ---
`features` | [RoadIncidentFeed](/spec-content/objects/RoadIncidentFeed.md)
`features` | [RoadRestrictionFeed](/spec-content/objects/RoadRestrictionFeed.md)
