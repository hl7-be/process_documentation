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
| `release request` | Request for a release (publication) of this IG | On the Release request issue of a release (see below). |

## Adding the labels to a repository

With the [GitHub CLI](https://cli.github.com/):

```
gh label create preapplied -R hl7-be/<repository> --description "Applied ahead of WG approval, for the group to confirm" --color F0B350
gh label create "CareSet change" -R hl7-be/<repository> --description "Asks for a change to the CareSet business document - to follow up with its authors" --color 5319E7
gh label create "release request" -R hl7-be/<repository> --description "Request for a release (publication) of this IG" --color 0E8A16
```

## Change process

Each change to an IG follows its issue through these steps, shown as the Status of the issue in the IG's project and by labels:

| Step | Status / label | Who | Recorded as |
|---|---|---|---|
| Submitted, triaged | Inbox, then To do | editor | the issue |
| Waiting for input | `waiting for info`, or `CareSet change` when the CareSet authors have to change the business document | business, CareSet authors | a comment |
| Resolved, change required | label `resolved` | working group | a **resolution comment** on the issue: "WG dd/mm/yyyy: <resolution>". The resolution comment is authoritative. |
| Resolved, no change | label `resolved`, issue closed as not planned | working group | a resolution comment |
| Technical correction | label `Technical Correction` | editor | no working group decision needed: no change of meaning |
| Applied before the decision | label `preapplied` | editor, then the working group confirms | the working group confirms with a resolution comment |
| Applied | pull request marked **ready for review** | editor | the editor validates that the change does what the resolution says, then marks the draft pull request ready |
| Published | the release pull request (`release-candidate` into the default branch) says `Closes #n`, and the issue closes | editor | the Release request issue |

Rules:

- A pull request stays a draft until its issue is `resolved`, or labelled `preapplied` or `Technical Correction`.
- The editor validates the change against the resolution before marking the pull request ready; only ready pull requests are merged.
- Every commit names its issue (`#n`). Every pull request names its issues: `Closes #n` when merging it fully resolves the issue, `Part of #n` otherwise.
- Decisions are recorded as a resolution comment on the issue, with the date of the working group, not only in the minutes. There is no vote.
- The working group agenda lists the issues to decide, with the link to each pull request's changes.

## Requesting a release

A release of an IG is requested with a **Release request** issue in the IG repository (template `Release request`, label `release request`), one issue per release. It states:

- the version to publish, and the previous one;
- the content freeze and the target publication date;
- the content: the issues and pull requests in the release, each approved by the working group or labelled `preapplied`;
- breaking changes, and whether the implementation timeline for vaults and vendors starts for the new content;
- dependencies, and other IGs released at the same time;
- the release-candidate preview and its QA report;
- the approvals.

The changes go to the `release-candidate` branch. The release pull request (`release-candidate` into the default branch) says `Closes #<release request>`, and `Closes #n` for each issue it resolves.

The FHIR Validation Team schedules and approves the publication in a **Publication of …** issue in [validation-team](https://github.com/hl7-be/validation-team/issues), which links to the release request.
