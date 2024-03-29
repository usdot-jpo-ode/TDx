# RoadEventCoreDetails Object
The `RoadEventCoreDetails` object represents the core details of an event occurring on a roadway (i.e. a "road event") that is shared by all types of road events, such as incidents (see [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md)), detours (see [DetourRoadEvent](/spec-content/objects/DetourRoadEvent.md)) and road restrictions (see [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md)). The `RoadEventCoreDetails` cannot exist directly in a data feed and on its own does not represent a road event. It is used as the value of `core_details` property on every specific type of road event, each of which is represented by its own object.

This object was initially developed for the [WZDx Specification](https://github.com/usdot-jpo-ode/wzdx).

## Properties
Name | Type | Description | Conformance | Notes
--- | --- | --- | --- | ---
`event_type` | [EventType](/spec-content/enumerated-types/EventType.md) | The type/classification of road event. | Required |
`data_source_id` | String | Identifies the data source from which the road event originates. | Required | Please see [Business Rule](/Creating_a_TDx_Feed.md#business-rules) #4.
`road_names` | Array; [String] | A list of publicly known names of the road on which the event occurs. This may include the road number designated by a jurisdiction such as a county, state or interstate (e.g. I-5, VT 133). | Required |
`direction` | [Direction](/spec-content/enumerated-types/Direction.md) | The digitization direction of the road that is impacted by the event. This value is based on the standard naming for US roadways and indicates the direction of the traffic flow regardless of the real heading angle. | Required | Example `northbound` (for I-5 North)
`related_road_events` | Array; [[RelatedRoadEvent](/spec-content/objects/RelatedRoadEvent.md)] | A list describing road events which are related to this road event. Examples of related road event include but are not limited to the sequence along the roadway,  related detours or other road events that encompass a similar work area. | Optional |
`name` | String | A human-readable name for the road event. | Optional |
`description` | String | Short free text description of road event. | Optional | 
`creation_date` | String; [date-time](https://tools.ietf.org/html/draft-handrews-json-schema-validation-01#section-7.3.1) | The UTC time and date when the activity or event was created. | Optional | All datetime formats shall follow [RFC 3339 Section 5.6](https://tools.ietf.org/html/rfc3339#section-5.6). Example: `2016-11-03T19:37:00Z`. <br />Please see [Business Rule](/Creating_a_TDx_Feed.md#business-rules) #5.
`update_date` | String; [date-time](https://tools.ietf.org/html/draft-handrews-json-schema-validation-01#section-7.3.1) | The UTC date and time when any information in the [RoadEventFeature](/spec-content/objects/RoadEventFeature.md) (including child objects) that the RoadEventCoreDetails applies to was most recently updated or confirmed as up to date. | Optional | All datetime formats shall follow [RFC 3339 Section 5.6](https://tools.ietf.org/html/rfc3339#section-5.6). Example: `2016-11-03T19:37:00Z`. <br />Please see [Business Rule](/Creating_a_TDx_Feed.md#business-rules) #5.
`relationship` (DEPRECATED) | [Relationship](/spec-content/objects/Relationship.md) | *This property is deprecated and will be removed in a future release, use `related_road_events` instead.* Identifies both sequential and hierarchical relationships between the road events and other entities. For example, a relationship can be used to link multiple road events to a common 'parent', such as a project or phase, or identify a sequence of road events | Optional | 

## Used By
Property | Object
--- | ---
`core_details` | [DetourRoadEvent](/spec-content/objects/DetourRoadEvent.md)
`core_details` | [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md)
`core_details` | [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md)

## Important Notes
The value of the `RoadEventCoreDetails`'s `data_source_id` property MUST match the value of the `data_source_id` property of a [FeedDataSource](/spec-content/objects/FeedDataSource.md) that is included in the same TDx GeoJSON document.
