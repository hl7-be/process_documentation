---
title: Standardisation process
has_children: true
has_grandchildren: true
nav_order: 10
---

# Publication

The publication process starts with a [project initiation](project_initiation.html) phase, which starts with a proposal that describes the content, and is evaluated by the working parties.

This proposal, which can be submitted by any institution, is validated by the HL7 Validation Working Group, which designates and/or summons one of the [HL7 Belgium FHIR Working Groups](hl7_be_wgs.html) for working on the artifacts. 


```plantuml!
@startuml
!pragma teoz true
hide footbox
actor person as "Person"
participant inst as "Institution"

box "HL7 Belgium" #FDD 
participant val as "Validation\nWorking group"
participant hl7 as "FHIR\nWorking group"
end box
participant eHealth as "eHealth" #bdf

group Project Initiation 
inst -> val: Project Proposal
val -> hl7: Assign working group
end

group Specification Development
person --> hl7 : (feedback)
& inst --> hl7 

group Work on profiles
activate hl7
hl7 -> hl7: work on standard
note left of hl7 #ffc
Development
work 
package
end note
deactivate hl7
end
end
...

group Publication
hl7 -> val: Submit package
activate val
val -> val : Prepare publication
val -> eHealth : Submit for publication
deactivate val
eHealth ->  : Publish
note right of eHealth #CFC
Official
release
end note
end



@enduml

```




