# Restriction Object
The `Restriction` object describes a restriction on a roadway or lane. This object is used by the [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md), [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md) and [Lane](/spec-content/objects/Lane.md) objects.

## Properties
Name | Type | Description | Conformance | Notes
--- | --- | --- | --- | ---
`type` | [RestrictionType](/spec-content/enumerated-types/RestrictionType.md) | The type of restriction being enforced. | Required |
`value` | Number | A value associated with the restriction, if applicable. | Optional | For example, if `type` is `reduced-height`, `value` and `unit` together would allow indicating what value the height was reduced to.
`unit` | [UnitOfMeasurement](/spec-content/enumerated-types/UnitOfMeasurement.md) | Unit of measurement for the restriction `value`, if applicable. | Conditional: required if `value` is not null. |
 
## Used By
Property | Object
--- | ---
`restrictions` | [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md)
`restrictions` | [Lane](/spec-content/objects/Lane.md)
`restrictions` | [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md)
