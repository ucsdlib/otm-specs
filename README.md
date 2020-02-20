# One to Many (OTM) Specifications

[[Reading View](https://ucsdlib.github.io/otm-specs/)] | [[Source View](https://github.com/ucsdlib/otm-specs)]

## Introduction
The wide adoption of digital repository software by cultural heritage organizations has led to significant increases in
effective management and access to digital assets. While these software systems may provide some digital preservation
features, the digital materials and their associated metadata managed by such systems need to be preserved in a way that
ensures they will persist over time. This project addresses this need by developing a specification for an integration model
that will allow libraries and archives to seamlessly deposit system content into distributed digital preservation systems
(DDPs) such as Chronopolis, APTrust, and LOCKSS. This project is funded by the Andrew W. Mellon Foundation.

More information about the project [can be found on the project wiki](https://wiki.lyrasis.org/display/OTM)

The members of the OTM project team are listed on the [Team Roles and Responsibilities page](https://wiki.lyrasis.org/display/OTM/Team+Roles+and+Responsibilities)

## Specifications
The One To Many (OTM) Specification defines two APIs to support communication between digital content repository systems
(Repository) and distributed digital preservation systems (DDP). These APIs work in tandem to allow content captured in
Repository systems to be copied to DDP systems for preservation. The two APIs are the [OTM Gateway
API](otm-gateway.html) (Gateway) for the Repository and the [OTM Bridge API](otm-bridge.html) (Bridge) for the DDP. The
Gateway and the Bridge APIs handle intermediary communication between the Repository and DDP and allow each system to operate
without any knowledge of the internals of the other system. Each API is designed to facilitate deployment either as part of
or extension to the Repository (in the case of the Gateway) or the DDP (in the case of the Bridge) or as a stand-alone
application. They each provide an HTTP-based approach for authentication, communication, and data transfer.

* [OTM Preservation Workflow](preservation-workflow.html) - An overview of the entire preservation process (start here!)
* [OTM Gateway API Specification](otm-gateway.html) - The preservation Gateway functions as an aggregating cache for preservation requests originating with a repository and destined for a DDP via the OTM Bridge
* [OTM Bridge API Specification](otm-bridge.html) - The Bridge provides a consistent interface for systems (including repositories) to integrate with DDP platforms; the Bridge also serves as a staging point for content being transferred into or out of a DDP
* [OTM Audit Events](audit-appendix.html) - A listing of preservation events that occur as part the workflow that may be captured by the DDP and made available through the Bridge

### Status of the Specifications
These specifications were created as part of the [One to Many grant](https://mellon.org/grants/grants-database/grants/university-of-california-at-san-diego/1805-05809/),
funded by the Andrew W. Mellon Foundation. The goals
and scope of this grant are described in [One to Many Project Overview and Goals](https://wiki.lyrasis.org/display/OTM/Project+Overview+and+Goals).

These specifications aim to provide the structure and interaction patterns necessary to meet the [One to Many User Stories](https://wiki.lyrasis.org/display/OTM/User+Stories). The team sought to define the APIs with enough specificity to allow future implementation efforts to succeed in delivering systems that satisfy those user stories, while leaving flexibility for implementers to adjust to the needs of the development phase. Future versions of these specifications are expected as an outcome of any effort to implement them.

## Usage Requirements

#### Repository

In order for a Repository system to make use of an application which has been developed to implement the Gateway API Specification, the following requirements would need to be in place:

* The Gateway application must be deployed and made available to the Repository
* The Repository must support the addition of preservation targets (DDPs)
* The Repository must support the selection of content for preservation storage

The following are recommended capabilities for a Repository that is to make use of a Gateway, but not required:

* The Repository should support the selection of content for restore
* The Repository should display details about object preservation status

#### DDP

In order for a Distributed Digital Preservation system to make use of an application which has been developed to implement the Bridge API Specification, the following requirements would need to be in place:

* The DDP must deploy and run the Bridge application
* The DDP must provide the Bridge application access to a staging storage location that is also available to the DDP
* The DDP must Implement tooling to interact with the Bridge application API
* The DDP must support at least minimal versioning capability (ingesting, restoring, and deleting named filegroup versions)

## Usage Notes

* In order for a Gateway to communicate with a Bridge an account with associated access credentials must first be created in the Bridge by the Bridge administrator and those credentials communicated to the Gateway administrator. Creating accounts is accomplished via the [Add Account](otm-bridge.html#add-account) endpoint.
* There will be a one-to-one relationship between a Bridge account and a single Gateway application
* The method of application authentication and authorization may vary by API implementation

## License

This document is licensed under a [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/)
