## RoadRestrictionFeed Examples
The following example `RoadRestrictionFeed`s are provided:

### 1. Bridge Height Restriction
The [Bridge Height Restriction Example](/examples/RoadRestrictionFeed/bridge_height_restriction_linestring_example.geojson) shows the use of a [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md) to define a bridge clearance on a roadway.

- Defines three bridge height restrictions.
- Two restrictions (`id`s: `Bridge2`, `Bridge3`) are defined using only the required core details and basic event-level information.
- One restriction (`id`: `Bridge1`) also includes lane-level details with additional height restrictions values for individual lanes.