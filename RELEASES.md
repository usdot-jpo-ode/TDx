# TDx Specification v1.1
Released February 2023

## New Functionality
- Define the [RoadIncidentFeed](/spec-content/objects/RoadIncidentFeed.md) and [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md) to enable providing a feed of crashes, natural disasters, special events, and weather. 
- Add `vehicle_impact` property to the [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md)
- Incorporate changes made to the [Work Zone Data Exchange (WZDx) Specification](https://github.com/usdot-jpo-ode/wzdx) versions [4.1](https://github.com/usdot-jpo-ode/wzdx/tree/v4.1#wzdx-v41-september-2022) and [4.2](https://github.com/usdot-jpo-ode/wzdx/tree/v4.2#wzdx-v42-february-2023) adding new functionality to objects and enumerated types:
   - Recommend using Universally Unique Identifiers (UUID) for the `id` property of the [RoadEventFeature](/spec-content/objects/RoadEventFeature.md) and [FeedDataSource](/spec-content/objects/FeedDataSource.md), noting that a UUID may be required in the next major release.
   - Add `name` property to [RoadEventCoreDetails](/spec-content/objects/RoadEventCoreDetails.md) to allow providing a human-friendly name for a road event.
   - Add a `related_road_events` property (and new supporting object [RelatedRoadEvent](https://github.com/usdot-jpo-ode/wzdx/tree/v4.1/spec-content/objects/RelatedRoadEvent.md) and enumerated type [RelatedRoadEventType](/spec-content/enumerated-types/RelatedRoadEventType.md)) to the [RoadEventCoreDetails](/spec-content/objects/RoadEventCoreDetails.md) to allow explicitly defining relationships/connections between road events; this replaces the [Relationship](/spec-content/objects/Relationship.md) object concept.
   - Add the following values to the [Direction](/spec-content/enumerated-types/Direction.md) enumerated type: `inner-loop`, `outer-loop`, `undefined`, and `unknown`.
   - Add `no-passing` to the [RestrictionType](/spec-content/enumerated-types/RestrictionType.md) enumerated type.
   - Add `two-way-center-turn-lane` to the [LaneType](https://github.com/usdot-jpo-ode/wzdx/tree/v4.1/spec-content/enumerated-types/LaneType.md) enumerated type to replace the existing `center-left-turn-lane` with a more generic value.

## Refactoring
- Incorporate changes made to the [WZDx Specification](https://github.com/usdot-jpo-ode/wzdx) deprecating objects, properties, and enumerated type values utilized in this specification: 
   - Deprecate the `relationship` property on the [RoadEventCoreDetails](https://github.com/usdot-jpo-ode/wzdx/tree/v4.1/spec-content/objects/RoadEventCoreDetails.md); use the new `related_road_events` property instead.
   - Deprecate the `center-left-turn-lane` value in the [LaneType](https://github.com/usdot-jpo-ode/wzdx/tree/v4.1/spec-content/enumerated-types/LaneType.md) enumerated type; use the new `two-way-center-turn-lane` instead.

## Cleanup
- Incorporate changes made to [WZDx Specification](https://github.com/usdot-jpo-ode/wzdx) cleaning up objects and values utilized in this specification:
   - Expand the description of the `geometry` property on the [RoadEventFeature](/spec-content/objects/RoadEventFeature.md) object to clarify how geometry should be used to represent a road event.
   - Update the description of the `open` and `closed` enumerations of the [LaneStatus](https://github.com/usdot-jpo-ode/wzdx/tree/v4.2/spec-content/enumerated-types/LaneStatus.md) enumerated type.

# TDx Specification v1.0
Released December 2021 as WZDx v4.0

TDx version 1.0 implements defines the [RoadRestrictionFeed](/spec-content/objects/RoadRestrictionFeed.md). 

## Features
- Define the [RoadRestrictionFeed](https://github.com/usdot-jpo-ode/TDx/tree/v1.0/spec-content/objects/RoadRestrictionFeed.md) and [RestrictionRoadEvent](https://github.com/usdot-jpo-ode/TDx/tree/v1.0/spec-content/objects/RestrictionRoadEvent.md) to enable providing a feed of restrictions on roadways, such as bridge clearances, using objects and enumerations developed for the WZDx Specification (including [Restriction](https://github.com/usdot-jpo-ode/TDx/tree/v1.0/spec-content/objects/Restriction.md), [Lane](https://github.com/usdot-jpo-ode/TDx/tree/v1.0/spec-content/objects/Lane.md), [RoadEventCoreDetails](/spec-content/objects/RoadEventCoreDetails.md), [FeedInfo](https://github.com/usdot-jpo-ode/TDx/tree/v1.0/spec-content/objects/FeedInfo.md), and [FeedDataSource](https://github.com/usdot-jpo-ode/TDx/tree/v1.0/spec-content/objects/FeedDataSource.md))
