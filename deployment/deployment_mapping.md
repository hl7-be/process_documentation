---
layout: default
title: Deployment mapping
parent: Deployment tracking
grand_parent: Deployment
nav_order: 20
---

# Deployment tracking

Tracking implementations can be done by 
* Define a list of "officially-defined" capabilities
* For each system, document the capabilities that the system supports
  * Possibly as a result of an accreditation or testing process


For this, we can keep a catalog of CapabilityStatements:
1. The CapabilityStatement definitions, that can be used in the Belgian architecture
2. The CapabilityStatement instances of those definitions, representing a system's implementation of a capability.

To document this, we have an ImplementationGuide that describes how CapabilitySatement can be used for this:
[https://github.com/hl7-be/fhir-capability-map](https://github.com/hl7-be/fhir-capability-map).

With this structure, it becomes relatively easy to tag the instance with geographical coordinates, for example. This is demonstrated here: [https://hl7-be.github.io/fhir-capability-map/map/map.html](https://hl7-be.github.io/fhir-capability-map/map/map.html).



