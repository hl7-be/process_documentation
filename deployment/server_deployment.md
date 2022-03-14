---
layout: default
title: Server deployment
parent: Deployment
has_children: false
nav_order: 10
---

Server

* Ensure that your IG has no errors in the qa.html page
* make sure your package id is correct i.e. no dots or dashes
* use the BE template for generating the application.yaml file
* run the command line
```
 docker run -p 8080:8080 -e hapi.fhir.default_encoding=json -e "--spring.config.location=https://hl7belgium.org/profiles/ehealth/be-core/application.yaml" hapiproject/hapi:latest
```
