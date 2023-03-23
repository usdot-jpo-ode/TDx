# Creating a TDx Feed
This documents contains information to assist in creating a TDx data feed, such as the feed format, business rules, and validation tools.

## Feed Format and File Type
TDx feeds are formatted according to the [GeoJSON](https://geojson.org/) specification. The output of a TDx feed is a GeoJSON document (a `.geojson` file) that contains a single [GeoJSON FeatureCollection](https://datatracker.ietf.org/doc/html/rfc7946#section-3.3) which includes information about the feed (see the [FeedInfo Object](/spec-content/objects/FeedInfo.md)) and a list of [GeoJSON Feature](https://datatracker.ietf.org/doc/html/rfc7946#section-3.2)s describing entities specific to the type of feed, such as road restrictions.

### Why GeoJSON?
GeoJSON is the file format of choice because:

- It is a lightweight data exchange format.
- It is easy for humans to read and write.
- It is easy for machines to parse and generate.
- The format is designed to exchange spatial data.
- It is an open specification and does not carry licensing burdens.
- GeoJSON formatted-data is published as text files, so there is a low technological burden of entry.
- GeoJSON validation, mapping, and visualization tools already exist and will ease adoption by producers and consumers.

## Feed Content
TDx defines the content and structure of several data feeds. Each feed is described by a single root object with many child objects. The output of a TDx data feed is a GeoJSON file containing the feed object. TDx defines the following feed objects:

- `RoadRestrictionFeed` provides information about sections of roadways that have restrictions. Restriction types described by this specification are listed in the [RestrictionType](/spec-content/enumerated-types/RestrictionType.md) enumerated type.
- `RoadIncidentFeed` provides information about sections of roadways that are impacted by incidents or events such as collisions, special events, disasters, or winds. Incident types described by this specification are listed in the [IncidentType](/spec-content/enumerated-types/IncidentType.md) enumerated type.

*See the [/spec-content/README.md](/spec-content/README.md) for detailed information on all objects defined by TDx.*

## Business Rules
The following business rules help assure a standardized and interpretable use of the TDx specification. The specification describes the required structure and data fields to describe a road event, whereas business rules are additional requirements for using the TDx specification in a standard manner. Note that business rules are distinct from best practices in that the latter are suggestions and business rules are requirements that cannot be validated by the JSON schema.

1. An event must be segmented into separate [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md)s, [DetourRoadEvent](/spec-content/objects/DetourRoadEvent.md)s,  or [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md)s when the value of a required property or lane object changes. A complex event should be linked together using the `related_road_events` property on the [RoadEventCoreDetails](/spec-content/objects/RoadEventCoreDetails.md).
2. If the `lanes` property on the [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md) or [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md) is provided, it must include one entry for every lane in the road event. Providing lane information for only some of the lanes in a road event is not allowed.
3. A [Lane](/spec-content/objects/Lane.md) `order` value of 1 must represent the left-most lane and an increase in 1 must represent moving a single lane to the right.
4. The `data_source_id` value must match to the `data_source_id` property of a [FeedDataSource](/spec-content/objects/FeedDataSource.md) included within the same TDx GeoJSON document on the [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md)s, [DetourRoadEvent](/spec-content/objects/DetourRoadEvent.md)s, or [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md)s.
5. All dates and times must be expressed in UTC.

## Implementation Guidance

- Feed producers should include a completed road event with a verified start and end date in a public feed for at least an hour or one feed refresh cycle (whichever is longer) to help inform consumers that the road event has officially ended.

## Data Security Best Practices
This is a working list of best practices for standing up a TDx data feed assembled by the WZDx Technical Assistance Co-chairs. Please note that this list is not all encompassing; DOTs should consult with security experts for help with securing infrastructure components. **Please note that these are best practices only; not requirements.**

### REST Endpoint Security
If the TDx feed is set up as a REST Service endpoint, it is recommended that the only exposed endpoint in the REST service for the feed is a HTTP GET endpoint. If a provider wants to allow queries to the data using the request body rather than using URL parameters with a GET request, HTTP POST is also allowed. Exposing only a retrieval method and a post method will deter unauthorized users from attempting to delete or alter the existing TDx feed provided. All TDx endpoints should allow only read access. No public endpoint should be exposed that allows write access to the feed. 

### SSL (TLS)
In order to secure data in transit from the TDx feed to the recipient, building the data feed endpoint using a Secure Sockets Layer (SSL) certificate is highly recommended. This ensures that the connection between the host and the recipient is secure and that data received from the recipient can be trusted. 

### Cloud-hosted
Though all DOTs have infrastructure capabilities to host a TDx feed, it is recommended that the feed be cloud hosted on a trusted platform due to the following reasons:

* Security: Trusted cloud hosted providers such as Amazon Web Services, Google Cloud Platform, and Microsoft Azure all have hardened physical security as well as digital security best practices already in place. 
* Dedicated Denial of Service (DDoS) Prevention: DDoS attacks remain a very common form of hacking that are still used today. Cloud providers have built solid solutions that can handle DDoS attacks and prevent downtime. 
*	Scalable: As TDx feeds become more widely used, they may be hit much more frequently than other endpoints. Cloud hosting allows DOTs to easily scale to accommodate for more hits or usage of the endpoint. 
*	Load Balancing Solutions: Along with scaling physical hardware, load balancing allows DOTs the ability to scale the number of endpoints  serving up TDx data feeds. 

### Securing the Source of Truth
DOTs should consider the sources that are being used to build the TDx feeds and ensure that those systems are also following the same best practices listed as above. TDx feeds should be built from reliable data received from the field and trusted sources of data. 

## Data Validation

### JSON Schemas
The TDx Specification defines a JSON schema for each feed within the [schemas](/schemas) directory. The repository contains schemas for the following feeds:

#### Current Version (TDx 1.1)
- [TDx v1.1 RoadIncidentFeed](/schemas/1.1/RoadIncidentFeed.json)
- [TDx v1.1 RoadRestrictionFeed](/schemas/1.1/RoadRestrictionFeed.json)

#### Previous Versions
- [TDx v1.0 RoadRestrictionFeed](/schemas/1.0/RoadRestrictionFeed.json)
