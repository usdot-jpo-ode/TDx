# TypeOfIncident Object
The `TypeOfIncident` object describes an event that causees disruptions to expected operations.

## Properties
Property Name | Data Type | Description | Conformance | Notes
--- | --- | --- | --- | ---
`incident_category` | [IncidentCategory](/spec-content/enumerated-types/IncidentCategory.md) | The category of incident causing disruptions. | Required | 
`incident_type` | [IncidentType](/spec-content/enumerated-types/IncidentType.md) | The type incident causing disruptions. | Required | Value must belong to the [IncidentCategory](/spec-content/enumerated-types/IncidentCategory.md) indicated with `incident_category` - see Category column of [IncidentType](/spec-content/enumerated-types/IncidentType.md) table.
`description` | String | Short free text desciption of the type of incident. | Required | 

## Used By
Property | Object
--- | ---
`types_of_incident` | [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md)
