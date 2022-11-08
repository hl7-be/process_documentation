---
title: Specification publication
parent: Standardisation process
#has_children: true
nav_order: 3
---

# Publication of specifications

The publication of specifications is a final step after the the CI build is OK.

It follows the process described in the [FHIR wiki](https://confluence.hl7.org/display/FHIR/Maintaining+a+FHIR+IG+Publication) and requires some preparatory actions:
1. Establishing a set of repositories and branches to support the different steps, enable some automation while allowing human control over the entire process
1. setting up the supporting content for the IG publication steps.
1. preparing the site(s) where the IG content will be published - CI-build and releases






```plantuml!
@startuml
actor User
hide footbox
!pragma teoz true

box "\nGitHub repositories\n"
  box "CI Repo" #FFE
    participant main
    participant "CI-build" as gh
    participant "release\ncandidate\n(release_candidate)" as relc
  end box

  box "Publication Repo" #EFE
    participant "upcoming\nrelease\n(main)" as rels
    participant "site\ncontent\n(site)" as site
  end box

end box

box "Publication site" #EFF
participant "Release\nhttps://<site>" as relsite
end box

box "Dependencies" #FEE
participant "IG history\ntemplate" as hist
participant "IG\nRegistry" as reg

end box

group Setup
User -> main : setup IG
activate main
main --> main : build
main --> gh : deploy
& note right of gh #cfc
CI build is published
end note
end
deactivate main
...
group Iterate changes
User -> main : commit
activate main
main --> main : build
main --> gh : deploy
& note right of gh
If build is successful, CI build
is automatically updated
end note
end 
deactivate main

...
...

group Setup IG release
User -> site: setup IG release
& note right of site
webroot folder
publish.ini
org history templates
end note
'User -> main: add package-list.json
end

group Add a release
User -> main: create publication-request.json
relc -> relc: normal build

group Prepare release site
relc -> rels: pull\nrelease\ncandidate
activate rels
hist --> rels : pull\nig-history\ntemplate 
reg --> rels : pull\nig-registry 
site --> rels: pull\ncurrent\nreleases 

rels --> rels: go-publish
end

rels -> site : deploy
...
user -> rels : verify
...
rels -> relsite : deploy
rels -> reg : (create\nPR)
deactivate rels

end
@enduml
```

