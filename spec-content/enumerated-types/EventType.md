# EventType Enumerated Type
The type of a WZDx road event.

## Values
Value | Description
--- | ---
`detour` | A temporary rerouting of road users onto an existing trafficway to avoid a work zone or other impedance.<br><br>Source: https://mutcd.fhwa.dot.gov/htm/2009/part6/part6c.htm
`restriction` | A section of roadway that has limitations of how that section can be used.
`incident` | Incidents or events that close or restrict the use of road segments.

## Used By
Property | Object
--- | ---
`event_type` | [RoadEventCoreDetails](/spec-content/objects/RoadEventCoreDetails.md)
