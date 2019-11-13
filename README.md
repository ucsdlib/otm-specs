# One to Many (OTM) Specifications

[[Reading View](https://ucsdlib.github.io/otm-specs/)] | [[Source View](https://github.com/ucsdlib/otm-specs)]

## Introduction
The wide adoption of digital repository software by cultural heritage organizations has led to significant increases in
effective management and access to digital assets. While these software systems may provide some digital preservation
features, the digital materials and their associated metadata managed by such systems need to be preserved in a way that
ensures they will persist over time. This project addresses this need by developing a specification for an integration model
that will allow libraries and archives to seamlessly deposit system content into distributed digital preservation systems
(DDPs) such as Chronopolis, APTrust, and LOCKSS. This project is funded by the Mellon Foundation.

## Specifications
The One To Many (OTM) Specification defines two APIs to support communication between digital content repository systems
(Repository) and distributed digital preservation systems (DDP). These APIs work in tandem to allow content captured in
Repository systems to be transitioned to DDP systems for preservation. The two APIs are the OTM Repository Gateway API
(Gateway) for the Repository and the OTM Bridge API (Bridge) for the DDP. The Gateway and the Bridge APIs handle intermediary
communication between the Repository and DDP and allow each system to operate without any knowledge of the internals of the
other system. Each API is designed to facilitate deployment either as part of or extension to the Repository (in the case of
the Gateway) or the DDP (in the case of the Bridge) or as a stand-alone application. They each provide an HTTP-based approach
for authentication, communication, and data transfer.

* [OTM Gateway](otm-gateway.html)
* [OTM Bridge](otm-bridge.html)
* [OTM Audit Event Appendix](audit-appendix.html) (non-normative appendix)
* [OTM Preservation Workflow Appendix](preservation-workflow.html) (non-normative appendix)
