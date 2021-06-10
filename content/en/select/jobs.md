---
title: Jobs
description: ""
position: 1002
category: "SELECT"
assignmentTypes:
  [
    Direct assign (A),
    Inherit from Ancestor (B),
    Inherit from Team (C),
    Inherit from Team which has been added to Ancestor (D),
  ]
---

What is job's?

Jobs for teams discussion ([read here](https://app.clubhouse.io/kollekt/story/10008/jobs-for-teams))

## Determining a user's job

For now user can have 4 kind of assignment to selection

<list :items="assignmentTypes"></list>

The priority is:

```
B > D > A > C
```

## Jobs from teams

- Team users can have the same `role` and `job` as a selection user.
- Team `owner` can edit the team users (and admins can too)
- When a team gets added to a selection the team's users are added to the selection with the same role and job as they have on the team (if no conflicts exist).
- A selection users role / job can be overwritten for that selection (by adding a "manual" user).

- The `role` and `job` to use for a selection user is determined by the following hierarchy (1 = highest priority):

1. Manual added user
2. Team added user

### Conflicts

If a user is added by multiple teams they get the `role` and `job` by the following hierarchy (1 = highest priority)
Jobs:

1. Approval
2. Alignment
3. Feedback

Roles:

1. Owner
2. Member

- A link exists between the team and the selection.
- A new user added to a team is added to all selections where the team is added.
- Team users roles and jobs are synced across all existing selections, still obeying the above hierarchy for roles and jobs.

### Example 1

_Team Denmark_

- David: `Owner/Alignment`

_Team Sweden_

- David: `Member/Feedback`

Both team `Sweden` and `Denmark` are added to selection `Handover`.

`Handover`

- David: `Owner/Alignment`

Davids role is changed to `Member` on `Denmark`.

`Handover`

- David: `Member/Alignment`

Davids role is changed to `Owner` on selection `Handover` (By adding manual user for David)

`Handover`

- David: `Owner/Alignment`

Team `Denmark` and team `Sweden` are removed from selection `Handover`.
`Handover`

- David: `Owner/Alignment` (cause this is a manual user now)

### Example 2

_Team Denmark_

- David: `Owner/Alignment`

_Team Sweden_

- David: `Member/Feedback`

Team `Sweden` is added to selection `Handover`.

`Handover`

- David: `Member/Feedback`

Manual user for David is added to selection with role/job `Denied/None`.

`Handover`

- David: `Denied/None`.

Team `Denmark` is added to selection.

`Handover`

- David: `Denied/None`.

### Example 3

_Team Denmark_

- No members

Team `Denmark` is added to selection `Handover`.

`Handover`

- No members

David `Member/Feedback` is added to section `Handover`.

`Handover`

- David `Member/Feedback`.

Team `Denmark` is removed from selection `Handover`.

`Handover`

- No members
