---
title: IG repository setup
parent: Standardisation process
nav_order: 4
---

# GitHub setup of an IG repository

Every HL7 Belgium implementation guide repository on GitHub has the labels below, so issues and pull requests are marked the same way in every IG.

## Labels

| Label | Description | Use |
|---|---|---|
| `preapplied` | Applied ahead of WG approval, for the group to confirm | On a pull request whose change is applied before the working group has approved it. The editor asks the group to confirm it at the next meeting. Reserved for obvious gaps, and for changes the group understands faster when it sees them applied. |
| `CareSet change` | Asks for a change to the CareSet business document - to follow up with its authors | On an issue (and its pull request) where profiling shows that the CareSet business document should change: a cardinality FHIR cannot represent, an element to remove, editorial corrections. The issue lists the requested changes; the label lets the editor follow them up with the CareSet authors until the document is updated. |

## Adding the labels to a repository

With the [GitHub CLI](https://cli.github.com/):

```
gh label create preapplied -R hl7-be/<repository> --description "Applied ahead of WG approval, for the group to confirm" --color F0B350
gh label create "CareSet change" -R hl7-be/<repository> --description "Asks for a change to the CareSet business document - to follow up with its authors" --color 5319E7
```
