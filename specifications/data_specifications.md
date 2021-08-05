---
layout: default
title: Data Specifications
parent: Specifications
has_children: true
nav_order: 25
---

Specifying the data to be exchanged is a key part of interoperability specifications.

The process to specify data is:
1. Define a logical data model
2. Derive the profiles, using extensions as needed
3. Define and implement terminologies - valuesets and codesystems 



## Logical Data Models

Logical Data Models are defined in FHIR as an abstract representation of the data, independent from any technology implementation.  


### Logical Data Models and terminology bindings
Logical Data Models can include terminology bindings. This is the case when the values in the valueset have a "official" meaning - like marital status, or country codes, for example. In such cases, the codes are not only a FHIR technical consideration, but they are supposed to be the same across implementations, across technologies and standards.   

This means that when defining the logical models, these valuesets should also be defined.  


### Profiling from Logical Models
The following guidelines apply when creating profiles from a logical model

* All elements in the logical model shall be in the profile, as a Must Support
* The data type and cardinality of the all elements in the logical model shall be reflected on the profile
* Any terminology bindings that are in the logical model shall also be present in the profile - the valuesets used in the logical model  can also be used in the profile


