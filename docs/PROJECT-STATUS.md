# ENGINEERING LAB — Project Status

> Portfolio-level status is evidence-based. A status describes the maturity of the work, not its ambition.

**Last reviewed:** 2026-11-11  
**Portfolio hub:** Active  
**Status vocabulary:** Proposed · Planned · Discovery · In Progress · In Review · Blocked · Complete · Maintained · Paused · Archived

## Portfolio overview

| Area | Current state | Evidence / note |
|---|---|---|
| Portfolio documentation foundation | In Progress | Core architecture, design, integration, standards, roadmap and ADR documents are present |
| Shared design system | Specification established | Design tokens and theme behaviour are documented; no shared component package or live theme switch is claimed |
| Engineering standards | Established as guidance | Standards are documented; adoption must be verified in each product |
| Integration strategy | Established as guidance | Contract patterns are documented; proposed integrations are not yet implemented |
| Product catalogue | Established | Catalogue describes the planned portfolio; entries are not evidence of implementation |

## Project dashboard

| Project | Status | Current milestone | Blockers / dependencies | Latest evidence | Next action |
|---|---|---|---|---|---|
| ENGINEERING LAB | In Progress | Portfolio foundation | None recorded | Core documentation and ADRs committed to the hub | Complete tracking templates and link them from the homepage |
| AEGIS | In Progress | Baseline verification and operational hardening ([consolidated AEGIS record](projects/AEGIS.md)) | Port visibility review, endpoint-specific authorization matrix, local test reconciliation, backup/restore evidence | 10–11 Nov checkpoint: non-root/read-only container controls, persistent SQLite after restart, SQLite integrity and foreign-key checks, pip check, selected API role outcomes, dashboard rendering, and five successful latest CI workflows recorded in the AEGIS repository and summarized in the ENGINEERING LAB log | Resume in the AEGIS development conversation: inspect working tree first, then complete the outstanding checks; do not rebuild or repeat verified checks without cause |
| SENTINEL QA | Planned | Discovery and technical specification | AEGIS API contract should be reviewed before integration testing is designed | No implementation recorded in this portfolio tracker | Define MVP scope, architecture and acceptance criteria |
| MERIDIAN | Planned | Discovery | Depends on requirements and technology selection | No implementation recorded in this portfolio tracker | Write problem statement and domain model |
| ORBIT | Planned | Discovery | Clarify boundary with FLOWSTATE | No implementation recorded in this portfolio tracker | Define the visual builder's distinct scope |
| All other catalogue projects | Planned | Not scheduled | Prioritisation and capacity | Catalogue entries only | Promote a project only when it is selected for active work |

> A row marked Planned or Discovery is not an implemented product. Update this dashboard only when repository evidence supports the change.

## Status definitions

- **Proposed:** An idea under consideration; not yet selected.
- **Planned:** Selected for future work, but implementation has not started.
- **Discovery:** Requirements, risks, feasibility or architecture are being investigated.
- **In Progress:** Work has started and there is current, verifiable implementation activity.
- **In Review:** A defined change is awaiting review or acceptance.
- **Blocked:** Progress depends on an identified unresolved issue.
- **Complete:** A specifically defined milestone meets its acceptance criteria. This does not imply the entire product is complete.
- **Maintained:** The product is in a stable maintenance mode with ongoing support.
- **Paused:** Work has intentionally stopped; record why and what would restart it.
- **Archived:** Work is retired and no longer actively maintained.

## Update protocol

For every meaningful status change:

1. Verify the relevant repository, branch and current commit.
2. Identify the milestone or feature that changed.
3. Record the evidence: commit, pull request, passing test run, release, demo or other reproducible artifact.
4. Update the project row and the project's own tracker.
5. Record blockers and dependencies explicitly.
6. Do not mark a milestone Complete until its acceptance criteria and required tests have passed.
7. Add a dated entry to the development log for significant decisions or completed work.

## Review cadence

- Review active project rows during the weekly planning session.
- Review planned projects when prioritisation changes, not merely to make the table look busy.
- Reconcile this dashboard with repository evidence before publishing portfolio claims.
- Keep completed milestones in the history; do not erase useful delivery evidence.

## Current priorities

1. Complete the repository-wide documentation consistency review.
2. Resume AEGIS verification from the [consolidated AEGIS record](projects/AEGIS.md), without repeating checks already supported by evidence.
3. Define SENTINEL QA as the next major new product, beginning with discovery and a testable MVP.
4. Select further products based on learning value, feasibility and available time.

## Change history

| Date | Change |
|---|---|
| 2026-11-10 | Initial portfolio status dashboard created from the verified documentation foundation and known project context. |
| 2026-11-10 | Homepage navigation and roadmap status vocabulary aligned with the tracking system. |
| 2026-11-11 | Recorded the AEGIS 10–11 November engineering checkpoint and created a consolidated AEGIS project record in ENGINEERING LAB, linking the technical snapshot, feature inventory, verification ledger and remaining work. AEGIS implementation remains in its independent repository and dedicated development conversation. |
