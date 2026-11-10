# [PROJECT NAME] — Milestone and Feature Tracker

**Last reviewed:** [YYYY-MM-DD]  
**Project status:** [Status]  
**Current milestone:** [Milestone ID and title]  
**Project repository:** [URL]

## How to maintain this tracker

- Give each milestone and feature a stable identifier.
- Keep each feature small enough to implement, review and verify.
- Link GitHub issues and pull requests rather than duplicating their full discussion.
- Define acceptance criteria before implementation.
- Record evidence when work is complete.
- Use Blocked only with a named blocker and next action.
- Do not mark work Complete because code was written; verify the acceptance criteria.

## Status vocabulary

| Status | Meaning |
|---|---|
| Proposed | Suggested but not selected |
| Planned | Selected, not started |
| In Progress | Active implementation or investigation |
| In Review | Awaiting review or acceptance |
| Blocked | Cannot progress until a named dependency is resolved |
| Complete | Acceptance criteria verified with evidence |
| Deferred | Intentionally moved out of the current scope |

## Priority vocabulary

- **P0 — Critical:** Required for the milestone to function safely or at all.
- **P1 — High:** Essential to the intended MVP or major workflow.
- **P2 — Medium:** Valuable but not required for the initial milestone.
- **P3 — Low:** Enhancement or future consideration.

## Milestones

| ID | Milestone | Outcome | Status | Target / review date | Dependencies | Evidence |
|---|---|---|---|---|---|---|
| M-001 | [Name] | [Verifiable outcome] | [Status] | [Date] | [IDs or none] | [Link] |

## Feature backlog

| ID | Feature | Priority | Status | Milestone | Issue / PR | Owner |
|---|---|---|---|---|---|---|
| F-001 | [Feature name] | [P0–P3] | [Status] | [M-001] | [Link] | [Owner] |

## Feature detail

Copy this section for each substantial feature.

### [F-001] — [Feature name]

**Problem / user need:** [Why this feature is needed.]  
**Scope:** [What is included.]  
**Out of scope:** [What is excluded.]  
**Dependencies:** [Other features, services, decisions or none.]  
**Risks:** [Known risks.]

#### Acceptance criteria

- [ ] Given [context], when [action], then [observable result].
- [ ] Invalid or unauthorised input is handled safely.
- [ ] Relevant failure and recovery paths are tested.
- [ ] Documentation and operational notes are updated.

#### Verification plan

| Check | Command / method | Expected result | Actual evidence |
|---|---|---|---|
| [Test] | [Command or link] | [Expected] | [Link / result] |

#### Delivery record

- **Implementation PR:** [Link]
- **Commit / release:** [Link or identifier]
- **Test run:** [Link]
- **Demo:** [Link]
- **Completed on:** [YYYY-MM-DD]
- **Known limitations:** [Details]

## Blockers and risks

| ID | Description | Impact | Owner | Next action | Status |
|---|---|---|---|---|---|
| B-001 | [Blocker or risk] | [Impact] | [Owner] | [Action] | [Status] |

## Definition of milestone complete

A milestone may be marked Complete only when:

- [ ] All P0 and required P1 features meet their acceptance criteria.
- [ ] Required automated tests pass.
- [ ] Security, data integrity and failure behaviour have been reviewed for the scope.
- [ ] Documentation and configuration examples are current.
- [ ] A reproducible demo or verification record exists.
- [ ] Known limitations and deferred work are recorded.
- [ ] The relevant changes are integrated into the intended branch.

## Review history

| Date | Reviewer | Summary | Follow-up |
|---|---|---|---|
| [YYYY-MM-DD] | [Name] | [Summary] | [Action] |
