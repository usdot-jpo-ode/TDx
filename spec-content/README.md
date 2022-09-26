# TDx Specification Content
The TDx specification defines the content and structure of GeoJSON documents intended to be distributed as a data feed. Each GeoJSON document (colloquially "feed") contains a single feed root object. The specification defines the following feed objects:

- [RoadRestrictionFeed](/spec-content/objects/RoadRestrictionFeed.md): describes the location and details of restrictions on roadways.

Each feed object contains many layers of child objects. Together all the objects define the TDx feed. All TDx objects are located in the [objects](/spec-content/objects) subdirectory and listed in the [Objects](#objects) section of this document.

The value of certain object properties is restricted to a defined set of values called an **enumerated type**. Enumerated types are located in the [enumerated-types](/spec-content/enumerated-types) subdirectory and listed in the [Enumerated Types](#enumerated-types) section of this document.

Many of the objects and enumerated types used in the TDx Specification were initially developed for the [WZDx Specification](https://github.com/usdot-jpo-ode/wzdx).

## Objects
Each TDx object is described by a table of properties with following columns:

- **Name** - The property name.
- **Type** - The type of data being stored. This can be one of the JSON primative types (only `String`, `Number`, `Array` are used), `Integer`, as defined in the [JSON schema validation specification section 6.1 (Draft 07)](https://tools.ietf.org/html/draft-handrews-json-schema-validation-01#section-6.1), a formatted string as defined in [JSON schema validation specification section 7 (Draft 07)](https://datatracker.ietf.org/doc/html/draft-handrews-json-schema-validation-01#section-7.3), a [TDx Enumerated Type](#enumerated-types), a TDx Object, or a [GeoJSON Object](https://tools.ietf.org/html/rfc7946#section-3).
- **Description** - A description of the value of the property.
- **Conformance** - An indication of the requirement for including the property in a TDx GeoJSON document. There are three categories of conformance:
    - *Required* - The property must be included
    - *Optional* - The property may be ommitted
    - *Conditional* - The property's inclusion depends on the inclusion or value of a separate property
- **Notes** - Additional comments, guidance, notes for future consideration, or examples.

### List of Objects
This section provides a tabular list of all objects used in the TDx specification.

#### Feed-Level
The following objects are high-level and describe either a TDx feed or information about a TDx feed:

Object | Description
--- | ---
[FeedDataSource](/spec-content/objects/FeedDataSource.md) | Information about a specific data source used to build a work zone data feed.
[FeedInfo](/spec-content/objects/FeedInfo.md) | Information about a TDx feed such as metadata, contact information, and data sources.
[RoadRestrictionFeed](/spec-content/objects/RoadRestrictionFeed.md) | The root (highest-level) object of a **Road Restriction Feed** GeoJSON document.

#### Road Events
The following objects are used to describe events ocurring on roadways (road events) that impact the characteristics of the roadway and involve a change from the default state:

Object | Description
--- | ---
[Lane](/spec-content/objects/Lane.md) | An individual lane within a road event.
[RelatedRoadEvent](/spec-content/objects/RelatedRoadEvent.md) | Identification a road event that is related to the road event that the RelatedRoadEvent object occurs on.
[Restriction](/spec-content/objects/Restriction.md) | A restriction on a road event or lane, including type and value.
[RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md) | Describes a section of roadway and the limitations of how that section can be used.
[RoadEventCoreDetails](/spec-content/objects/RoadEventCoreDetails.md) | The core details of an event occurring on a roadway (i.e. a road event) that is shared by all types of road events. 
[RoadEventFeature](/spec-content/objects/RoadEventFeature.md) | The GeoJSON `Feature` container object for a TDx road event.
[Relationship](/spec-content/objects/Relationship.md) (DEPRECATED)| *All properties that use this object are deprecated so this object will be removed in a future release, use [RelatedRoadEvent](/spec-content/objects/RelatedRoadEvent.md) instead.* Identification of both sequential and hierarchical relationships between road events and other entities.

### Object Diagrams
The object diagrams below depict the relationship between the data objects for each TDx feed.

The object diagram below indicates the relationship between the data objects used in the **RoadRestrictionFeed**:

![TDx RoadRestrictionFeed object diagram](/images/TDx_RoadRestrictionFeed_object_diagram.png)

#### Updating the object diagram
When making changes to the specification, the object diagram needs to be updated as well. To modify the object diagram, open `/images/TDx_RoadRestrictionFeed_object_diagram.drawio` at https://app.diagrams.net (or any drawio editor). Make necessary changes to the diagram using the web editor, then download the `drawio` file and replace the appropriate file in the `/images` directory with the new file. Additionally **export** the diagram as a PNG, using the diagram name as the file name, and replace `/images/TDx_RoadRestrictionFeed_object_diagram.png` with the new image file.

## Enumerated Types
Many object properties are restricted to a finite set of values defined by an enumerated type. The enumerations for each enumerated type as well as what object properties it is used by is described in its own file in the [enumerated-types](/spec-content/enumerated-types) directory.

### List of Enumerated Types
This section provides a tabular list of all enumerated types used in the TDx specification.

#### Road Events
The following enumerated types are used by objects that describe road events:

Enumerated Type | Description
--- | ---
[Direction](/spec-content/enumerated-types/Direction.md) | The direction for a road event based on standard naming for US roads.
[EventType](/spec-content/enumerated-types/EventType.md) | The type of a TDx road event.
[LaneStatus](/spec-content/enumerated-types/LaneStatus.md) | The status of a lane for the traveling public.
[LaneType](/spec-content/enumerated-types/LaneType.md) | An indication of the type of lane or shoulder.
[RelatedRoadEventType](/spec-content/enumerated-types/RelatedRoadEventType.md) | The type of relationship with a road event that is being identified.
[RestrictionType](/spec-content/enumerated-types/RestrictionType.md) | The type of vehicle restriction on a roadway or lane.
[UnitOfMeasurement](/spec-content/enumerated-types/UnitOfMeasurement.md) | Unit of measurement (e.g. "pounds", "centimeters").
[VehicleImpact](/spec-content/enumerated-types/VehicleImpact.md) | The impact to vehicular lanes along a single road in a single direction.