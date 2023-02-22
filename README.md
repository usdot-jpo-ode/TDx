# Transportation Data Exchange (TDx)

This repository contains data specifications intented to harmonize sharing of information about transportation events and infrastructure between infrastructure owner operators and the public. The specifications here were initially created under the [Work Zone Data Exchange](https://github.com/usdot-jpo-ode/wzdx) project. 

## README Outline
- [Data Feeds](#data-feeds)
- [Repository Organization](#repostitory-organization)
- [Project Description](#project-description)
- [Contact Information](#contact-information)
- [Release Notes](#release-notes)
- [Getting Started](#getting-started)
- [JSON Schemas](#json-schemas)
- [Contributions](#contributions)
- [Versioning](#versioning)
- [License](#license)

## Data Feeds
TDx defines the structure and content of multiple distinct data feeds. Each feed is distributed as a single GeoJSON file and is represented by both human-friendly documentation in the [spec-content](/spec-content/) directory and a JSON Schema in [/schemas](/schemas/). Each feed is designed for a specific use case is are flexible and its use in practice can vary by application.

### List of Data Feeds
Feed Name | Description | Producer | Consumer | Uses | Content
--- | --- | --- | --- | --- | ---
`RoadIncidentFeed` | Provides information about incidents or events that close or restrict the use of a road segment. | Transportation Authorities like Tribal, Local, State, or Federal Agencies. | Traveling public via third parties such as mapping companies and CAVs. | Increased awareness; Route planning; Driver, Passenger, and Road-User Safety. | Incident and detour road events (see [IncidentRoadEvent](/spec-content/objects/IncidentRoadEvent.md) and [DetourRoadEvent](/spec-content/objects/DetourRoadEvent.md)).
`RoadRestrictionFeed` | Provides information about sections of roadways that have restrictions. Restriction types described by this specification are listed in the [RestrictionType](/spec-content/enumerated-types/RestrictionType.md) enumerated type. | Transportation Authorities like Tribal, Local, State, or Federal Agencies. | Traveling public via third parties such as mapping companies and CAVs. | Increased awareness; Route planning; Driver, Passenger, and Road-User Safety; Increased Efficiency; Reduced Damage to Infrastructure. | Restriction road events (see [RestrictionRoadEvent](/spec-content/objects/RestrictionRoadEvent.md)).


## Repostitory Organization
The TDx Specification repository contains several files and subdirectories.

### Directories
1. [examples](/examples): example GeoJSON documents from TDx data feeds. [examples/README.md](/examples/README.md) describes the content of this directory in detail.
1. [images](/images): the images that are referenced by other Markdown files in the repository.
1. [schemas](/schemas): contains [JSON Schema](https://json-schema.org/)s for each of the feeds defined by TDx for feed validation.
1. [spec-content](/spec-content): details the data content of the TDx specification, including objects, property names and types, and enumerated types. [spec-content/README.md](/spec-content/README.md) describes the content of this directory in detail.

### Files
1. [LICENSE](/LICENSE): the Creative Commons Zero v1.0 Universal license that the repository is licensed under.
2. [README.md](/README.md) (this document): information about the TDx effort and navigating the repository.
3. [RELEASES.md](/RELEASES.md): detailed information about every release of the TDx specification.

## Project Description

**What is the TDx Specification?**
The Transportation Data Exchange (TDx) Specification enables infrastructure owners and operators (IOOs) to make harmonized transportation data available for third-party use. The intent is to make travel safer and more efficient through ubiquitous access to data on hazards like road restrictions. 

**How was TDx started?**
The TDx Road Restriction Feed was created as an extension of the Work Zone Data Exchange (WZDx) model. WZDx created a specification for communicating work zone and detour information using GeoJSON files and features called "road events." The Road Restriction Feed extended that model to communicate sections of roadway that feature permanent height, weight, or other restrictions. 

**How can I get help with implementation?**
Review [Creating_a_TDx_Feed.md](/Creating_a_TDx_Feed.md) which contains information to assist in creating a TDx data feed, such as the feed format, business rules, and validation tools.

This project repository will be continually updated with resources to help with implementation - in the meantime, please make a [new GitHub discussion](https://github.com/usdot-jpo-ode/tdx/discussions/new) if you need help implementing the TDx Specification or have questions.

## Contact Information

Contact Name: ITS JPO

Contact Information: [avdx@dot.gov](mailto:avdx@dot.gov)


## Getting Started

Feedback and comments on the TDx v1.0 Specification are welcome. Comments can be made by posting a GitHub [Issue](https://github.com/usdot-jpo-ode/TDx/issues) or [Discussion](https://github.com/usdot-jpo-ode/TDx/discussions), while suggested changes can be made using a [Pull Request](https://github.com/usdot-jpo-ode/TDx/pulls).

1. Learn about using GitHub as a [tool for collaboration and support](/create-feed/README.md#collaborate-via-github).
1. Use the [Specification Content](/spec-content) page to understand the data components of the specification.
1. Validate your feed output using the respective [JSON Schema](#json-schemas).
1. Publish your feed and tell us about it via avdx@dot.gov.

## JSON Schemas
The TDx Specification defines a JSON schema for each feed within the [schemas](/schemas) directory. Schemas can be used to validate a TDx feed document for compliance to the specification. The repository contains schemas for the following feeds:

### Current Version (TDx 1.1)
- [TDx v1.1 RoadIncidentFeed](/schemas/1.1/RoadIncidentFeed.json)
- [TDx v1.1 RoadRestrictionFeed](/schemas/1.1/RoadRestrictionFeed.json)

### Previous Versions
- [TDx v1.0 RoadRestrictionFeed](/schemas/1.0/RoadRestrictionFeed.json)

## Contributions

**How do I contribute to the TDx Specification?**

- Report bugs and request features via [GitHub Issues](https://github.com/usdot-jpo-ode/tdx/issues).
- Ask the TDx community for input on a question or propose an idea you have via [GithHub Discussions](https://github.com/usdot-jpo-ode/tdx/discussions).
- Create a [GitHub Pull Request](https://help.github.com/articles/creating-a-pull-request/) that implements new functionality or fixes a bug.
- Review and provide feedback on update issues/discussions/pull requests created by other users.
- Alternatively, [email us](mailto://avdx@dot.gov.) with any questions.
- Help us improve our best practices and formatting on GitHub.

## Versioning

The WZDx and TDx specifications use a major.minor versioning scheme, similar to [SemVer](https://semver.org/). The rules are as follows:

1. The minor version number must be incremented if new, backwards compatible fields/entities/enumerations are introduced or if any existing fields/entities/enumerations are marked as deprecated.
2. The major version number must be incremented if any backwards incompatible changes are introduced.
3. Neither version number shall be incremented for documentation changes/clarifications that have no effect on either the specification schema or the content or structure of a GeoJSON feed file which conforms to the specification.

To view available versions, refer to the [tags](https://github.com/usdot-jpo-ode/tdx/tags) section of this repository.

## License

The TDx project is in the worldwide public domain (i.e., in the public domain within the United States - copyright and related rights in the work worldwide are waived through the [CC0 1.0 Universal](https://creativecommons.org/share-your-work/public-domain/cc0/) public domain dedication). All contributions to this project will be released under the CC0 dedication. By submitting a pull request, you are agreeing to comply with the waiver of copyright interest. see [License](LICENSE) for more details.
