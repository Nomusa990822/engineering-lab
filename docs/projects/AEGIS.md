# AEGIS — ENGINEERING LAB Project Record

**Portfolio:** ENGINEERING LAB  
**Product:** AEGIS Security Platform  
**Record type:** Consolidated portfolio project brief, technical snapshot, milestone tracker and verification ledger  
**Portfolio status:** In Progress  
**Last reviewed:** 2026-11-11  
**Product repository:** https://github.com/Nomusa990822/aegis-security-platform  
**Inspected product revision:** `main` at `8fb3972b255c96cda479b270d164adf3ce21f455`  
**Detailed implementation workspace:** AEGIS's independent repository and its dedicated development conversation

> **Repository boundary:** This is the central AEGIS portfolio record and is maintained only in ENGINEERING LAB. Do not copy this record, the ENGINEERING LAB templates, or portfolio progress reports into the AEGIS Security Platform repository. AEGIS source code and its product runtime remain independent. Future AEGIS milestones are reported here after they are worked on and verified in the dedicated AEGIS workspace.

---

## 1. Executive summary

AEGIS is an independently maintained cybersecurity detection and response platform. Its current development foundation uses Python, FastAPI, Pydantic, SQLite and a JavaScript/HTML/CSS dashboard. The system ingests and validates security events, applies detection rules, manages alerts and investigations, enriches threat context, and provides a controlled analyst/approver response workflow with dry-run simulation and audit evidence.

The 10–11 November 2026 engineering checkpoint established evidence across container hardening, persistent storage, database integrity, dependency consistency, selected API authorization outcomes, dashboard rendering and automated CI workflows. A follow-up on 11 November also recorded 715 passing backend tests and verified a live synthetic event-to-alert-to-investigation path, including all five evidence links and the MITRE ATT&CK mapping.

**Current assessment:** AEGIS is an active engineering project with substantial implemented functionality and several successful verification gates. It is not yet appropriate to describe it as production-ready, independently penetration-tested, disaster-recovery tested, or proven effective against real-world threats. Important operational and endpoint-specific checks remain open.

This record consolidates the work completed so far. It is not a claim that all AEGIS features have been exhaustively tested.

## 2. Product purpose, goals and boundaries

### Purpose

Provide a defensive security platform for collecting security telemetry, identifying suspicious activity, presenting actionable alerts, supporting analyst investigation, and controlling response decisions.

### Goals represented in the current implementation

- Accept and validate security events through an API.
- Persist events and prevent duplicate processing where idempotency applies.
- Apply registered detection rules and correlate relevant activity.
- Present alerts and their lifecycle to an analyst.
- Enrich alerts with threat-intelligence context and MITRE ATT&CK references.
- Separate analyst response requests from approver decisions.
- Apply policy checks and support safe response simulation.
- Preserve response-related audit evidence.
- Provide a dashboard for security-event activity, alert distribution and system health.
- Support telemetry parsing for selected Linux SSH and Nginx sources.

### Explicit non-goals / claims not established

- No claim of production readiness or certification.
- No claim of comprehensive real-world detection accuracy or measured false-positive/false-negative rates.
- No claim that response actions have changed a real firewall, host, network or external system.
- No claim that all API routes have passed a complete authorization matrix.
- No claim of independent penetration-test completion.
- No claim of successful backup restoration or disaster recovery.
- No claim that every possible threat-intelligence provider failure or adversarial input has been exhaustively tested.

## 3. Technical specification snapshot

This section applies the relevant structure of the ENGINEERING LAB Technical Specification Template to the known AEGIS baseline. It is a current-state snapshot, not a replacement for detailed product implementation documentation.

### 3.1 System context and components

| Component / concern | Current understanding |
|---|---|
| API/backend | Python, FastAPI and Pydantic |
| Persistence | SQLite in the inspected development setup |
| User interface | JavaScript, HTML and CSS dashboard served at `/dashboard` |
| Event processing | Event ingestion, validation, deduplication/idempotency and persistence |
| Detection | Ten registered detection rules spanning authentication and network behaviour at the inspected revision |
| Alert workflow | Alert lifecycle, investigation functionality, evidence links and history |
| Threat context | Threat-intelligence enrichment, provider failure/timeout isolation, scoring and MITRE ATT&CK context |
| Response control | Analyst request, separate approver decision, policy checks and dry-run simulation |
| Audit evidence | Hash-chained response audit events and signed checkpoint/intent safeguards |
| Telemetry sources | Linux SSH and Nginx parsing/adapters |
| Runtime | Docker Compose container with persistent `/data` volume and health check |

The table describes capabilities present in the inspected source tree and session evidence. It does not imply every path has passed an end-to-end test.

### 3.2 Data and persistence

- SQLite database path observed in the container: `/data/aegis.db`.
- Compose configuration specifies a named `aegis-data:/data` volume.
- The database was observed to survive a container restart.
- SQLite integrity check returned `ok`.
- SQLite foreign-key check returned an empty result (`[]`), meaning no violations were reported by that check.

**Not yet demonstrated:** a verified backup artifact, restore into a clean target, integrity comparison after restore, or a documented recovery-time procedure.

### 3.3 Security and trust boundaries

Observed container controls in the inspected Compose configuration / session:
- Non-root runtime user `aegis`.
- Read-only container root filesystem.
- Linux capabilities dropped.
- `no-new-privileges` enabled.
- Temporary writable filesystem area provided separately.
- Persistent application data mounted at `/data`.
- HTTP health check configured.

API evidence is currently limited to selected endpoint/role outcomes. A full route-by-route authorization matrix remains open. Credentials and tokens must never be written into this portfolio record.

### 3.4 Dashboard and user experience

The dashboard was manually confirmed to render:
- AEGIS logo and product identity.
- Four overview metric cards.
- Security Event Activity chart.
- Alert Distribution chart.
- System Health section.

This was a manual visual confirmation, not a recorded browser-automation or accessibility test. The AEGIS visual identity is to be preserved; the shared ENGINEERING LAB design specification does not require an AEGIS redesign.

### 3.5 Testing approach

The verification programme should cover, as relevant:
- Unit tests for parsing, validation, detection and policy logic.
- Integration tests for persistence, alert lifecycle, enrichment and response workflow.
- API authentication and role authorization for every protected route.
- Negative and malformed-input cases.
- Database integrity and restart persistence.
- Container build and runtime security.
- Secret scanning and static analysis.
- Safe response simulation and audit-chain integrity.
- Backup and restore.
- Reproducible dashboard and remote-access checks.

A passing CI workflow only supports the scope of the jobs it actually ran. It is not a blanket guarantee of security or correctness.

## 4. Capability and feature inventory

The following inventory consolidates the capabilities identified in the inspected AEGIS source tree. Status labels distinguish presence in source from verification depth.

| Capability | Current record | Evidence / qualification |
|---|---|---|
| FastAPI backend and Pydantic validation | Implemented in inspected revision | Source tree inspection |
| SQLite persistence | Implemented; selected runtime checks passed | Persistent database survived restart; integrity check passed |
| Event ingestion and validation | Present | Source tree inspection; broader adversarial coverage not asserted here |
| Event deduplication / idempotency | Present | Source tree inspection |
| Detection rules | Ten registered rules present | Authentication and network-behaviour coverage in inspected revision |
| Detection correlation | Present | Source tree inspection |
| Alert lifecycle and investigation | Present | Source tree inspection; complete route authorization remains to be checked |
| Threat-intelligence enrichment | Present | Includes provider failure/timeout isolation and scoring in inspected tree |
| MITRE ATT&CK context | Present | Source tree inspection |
| Analyst / approver response separation | Present | Selected role outcomes checked |
| Policy-controlled response | Present | Source tree inspection |
| Dry-run response simulation | Present | Inspected response record was rejected and not executed |
| Hash-chained response audit evidence | Present | Source tree inspection; full independent tamper/recovery review not claimed |
| Signed checkpoint / intent safeguards | Present | Source tree inspection |
| Linux SSH telemetry adapter | Present | Source tree inspection |
| Nginx telemetry adapter | Present | Source tree inspection |
| JavaScript dashboard | Present and manually rendered | Manual visual confirmation only |
| Docker runtime hardening | Configured and runtime-observed | Non-root, read-only root FS, dropped capabilities, no-new-privileges |
| Persistent data volume | Configured and restart-observed | `/data/aegis.db` survived restart |
| Automated CI security/quality workflows | Five latest workflows succeeded at inspected revision | Workflow evidence linked below |

## 5. Verification ledger — evidence recorded by 11 November 2026

### 5.1 Runtime, container and persistence

| Check | Recorded result | Evidence strength / limitation |
|---|---|---|
| Container health after restart | Healthy | Docker Compose status observed |
| Runtime user | `aegis` (non-root) | Container runtime inspection |
| Root filesystem | Read-only | Compose configuration and runtime setup |
| Linux capabilities | Dropped | Compose configuration |
| Privilege escalation | Disabled with `no-new-privileges` | Compose configuration |
| Persistent data volume | `aegis-data:/data` | Compose configuration |
| SQLite survives restart | Yes | `/data/aegis.db` remained present after restart; observed size approximately 176 KB and owner `aegis:aegis` |
| SQLite integrity | `ok` | `PRAGMA integrity_check` |
| SQLite foreign keys | `[]` | `PRAGMA foreign_key_check`; no violations returned |

### 5.2 Dependency consistency

| Check | Recorded result |
|---|---|
| `python -m pip check` | `No broken requirements found.` |

This is a dependency consistency check, not a vulnerability-free dependency claim.

### 5.3 API authorization and response workflow

| Scenario | Observed result | Limitation |
|---|---|---|
| Request without bearer token | HTTP 401 | Selected endpoint only |
| Authenticated analyst request | HTTP 200 | Selected endpoint only |
| Authenticated approver request | HTTP 200 | Selected endpoint only |
| Role-restricted operation | HTTP 403 | Selected operation only |
| Response record ID 1 | Status `rejected`; `simulated=false`; `executed=false` | Confirms this record was not simulated or executed; does not establish all response paths |

Do not generalise these selected results to every route. The full route-specific authorization matrix is still outstanding.

### 5.4 Automated CI evidence

At product revision `8fb3972b255c96cda479b270d164adf3ce21f455`, the five latest inspected workflows completed successfully:

| Workflow | Run | Recorded scope |
|---|---:|---|
| Backend tests | [Run 195](https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027729) | Lockfile/dependency checks and backend test suite |
| Container image security | [Run 63](https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027765) | Image build, CycloneDX SBOM generation/validation and Trivy HIGH/CRITICAL fixable-vulnerability gate |
| API security baseline | [Run 22](https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027781) | OWASP ZAP baseline using analyst and approver credentials |
| Secret scanning | [Run 30](https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027677) | Gitleaks scan across Git history |
| CodeQL | [Run 38](https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027792) | Python and JavaScript/TypeScript analysis |

Successful workflow completion means those configured jobs completed successfully. It does not establish zero vulnerabilities, comprehensive penetration testing, or production readiness. The container configuration also documents a Trivy exception for CVE-2025-47273 associated with setuptools metadata in the upstream `python:3.14-slim` image; the final image removes setuptools package files and metadata and asserts that no setuptools distribution remains. This is a documented, scoped exception—not a claim that the upstream finding never existed—and it should be revisited if the base image or removal checks change.

### 5.5 Automated test results

- Complete backend pytest suite: **715 passed**.
- Focused response tests: **45 passed**.
- Focused audit-related tests: **167 passed**.

The two focused results are subsets of the full suite and must not be added to the 715-test total. These results are already recorded; do not rerun pytest unless a source change or a specific regression gives a reason. The exact commit/working-tree association for the 715-test run should be reconciled before a future release or source modification.

### 5.6 Live event-to-investigation verification

A read-only inspection of the running Docker service on 11 November 2026 confirmed the following synthetic demonstration workflow:

| Check | Observed result | Qualification |
|---|---|---|
| `GET /api/v1/events?limit=5` | Five events returned | All were authentication failures from source system `aegis-demo` |
| `GET /api/v1/alerts?limit=5` | One alert returned | High-severity `Brute Force Authentication Detection`, rule `AEGIS-AUTH-001` |
| Detection threshold | Five failures within five minutes | Alert description and source/account values matched the event sequence |
| `GET /api/v1/alerts/1/investigation` | Investigation details returned | Five of five underlying events were linked as evidence |
| MITRE ATT&CK enrichment | Mapped to `T1110.001 — Password Guessing` | Parent technique `T1110`, tactic `Credential Access` (`TA0006`) |
| Investigation record | Note and timeline returned | Analyst actions, status changes, evidence links and investigation note were present |
| Current alert status | `investigating` | Timeline also retained the earlier resolved and reopened transitions |

**Safety and scope:** These were synthetic demonstration events from `aegis-demo`, using reserved documentation IP `198.51.100.42`. This verifies the controlled demonstration path, not detection against real malicious traffic or real-world detection efficacy. The inspection was read-only and did not create new events or modify the alert.

## 6. Milestone tracker

| ID | Milestone | Status | Completion evidence / remaining work |
|---|---|---|---|
| AEGIS-M01 | Core application and dashboard foundation | In Progress | Backend, SQLite and dashboard are present; continue to preserve working functionality |
| AEGIS-M02 | Event ingestion, detection and alert workflow | In Progress | Five synthetic authentication failures produced the expected high-severity alert; all five events were linked to its investigation, with MITRE T1110.001 mapping and timeline evidence. Broader detection efficacy remains unmeasured |
| AEGIS-M03 | Threat context and controlled response workflow | In Progress | Enrichment, analyst/approver separation, policy checks and dry-run capability are present; expand route-specific and negative-path verification |
| AEGIS-M04 | Container hardening and persistent runtime | In Progress | Key controls configured and observed; add backup/restore and operational runbook evidence |
| AEGIS-M05 | CI quality and security baseline | In Progress | Five latest workflows succeeded at inspected revision; review findings and maintain repeatability |
| AEGIS-M06 | Operational verification and recovery | Planned / outstanding | Port exposure review, full authorization matrix, tested-revision/working-tree reconciliation, independent backup/restore and remote-access test remain |

A milestone is not marked Complete merely because its implementation exists. Acceptance requires current evidence for its defined scope.

## 7. Outstanding verification and next actions

Resume in the dedicated AEGIS development conversation. Work through this list in order and record actual results.

1. **Reconcile the working tree before changes.** Inspect `git status --short` and `git log -1 --oneline`; identify any uncommitted work and preserve it.
2. **Review Codespaces port visibility.** Inspect port 8000 visibility and retain private access unless an intentional, justified review requires otherwise.
3. **Complete endpoint-specific authorization checks.** For investigation and response routes, test no token, analyst credentials and approver credentials. Record HTTP method, path, expected status, actual status and response assertion. Do not expose credentials in logs.
4. **Reconcile the test result to a source revision.** The full backend suite has already passed (715 tests); do not rerun it without a source change or specific regression. Confirm which commit/working-tree state the recorded result represents when the working tree is next inspected.
5. **Perform a backup-and-restore exercise.** Create a backup, restore it into a separate clean target, verify database integrity and representative records, and document the procedure and result. A persistent Docker volume is not an independent backup.
6. **Test intended remote-device access safely.** Confirm that access works as intended without weakening authentication, authorization or network exposure controls.
7. **Capture genuine dashboard evidence where useful.** Use actual application screenshots; label the date/revision and do not substitute mock-ups.
8. **Reconcile this portfolio record.** Update only after the corresponding work has actually been performed and evidence is available.

## 8. Risks, limitations and dependencies

| ID | Risk / limitation | Current impact | Next action |
|---|---|---|---|
| R-01 | API authorization coverage is incomplete in the retained evidence | A role check on selected endpoints cannot establish all route permissions | Complete the route matrix |
| R-02 | Backup/restore has not been demonstrated | Persistence after restart is not disaster recovery | Run and document restore test |
| R-03 | Exact source revision for the retained local test result is not recorded | 715 backend tests passed, but the tested commit/working-tree state must be tied to the result | Reconcile test evidence against the next working-tree inspection; rerun only if justified |
| R-04 | Codespaces port exposure has not been fully reconciled | Remote accessibility could unintentionally widen exposure | Inspect visibility and access controls |
| R-05 | Real response execution is not established | Do not claim live containment or remediation | Keep testing in simulation unless explicitly designed and authorized |
| R-06 | Detection efficacy is not measured | Rules existing does not prove real-world accuracy | Build a controlled labelled evaluation dataset before making efficacy claims |
| R-07 | No independent penetration test is recorded | CI scanners are not a substitute for independent assessment | Scope and conduct a separate authorized review when appropriate |

## 9. Evidence links and source of truth

- **Product repository:** https://github.com/Nomusa990822/aegis-security-platform
- **Inspected product revision:** https://github.com/Nomusa990822/aegis-security-platform/commit/8fb3972b255c96cda479b270d164adf3ce21f455
- **Backend CI:** https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027729
- **Container security CI:** https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027765
- **API security baseline:** https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027781
- **Secret scanning:** https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027677
- **CodeQL:** https://github.com/Nomusa990822/aegis-security-platform/actions/runs/42920027792
- **Dated portfolio checkpoint:** [2026-11-11 AEGIS development log](../development-log/2026-11-11-aegis.md)
- **Portfolio dashboard:** [Project status](../PROJECT-STATUS.md)
- **Portfolio delivery plan:** [Roadmap](../../ROADMAP.md)

The product repository and its GitHub Actions are evidence sources. This consolidated file is the ENGINEERING LAB portfolio record; it does not replace product source code, test reports or detailed implementation notes.

## 10. Documentation-template coverage

The existing ENGINEERING LAB templates have been applied as sections of this single consolidated record to avoid creating multiple disconnected AEGIS documents:

| ENGINEERING LAB template | Where it is represented here |
|---|---|
| Project README template | Sections 1–2, 9 and the project metadata above |
| Technical specification template | Sections 2–3, 8 and 9 |
| Feature / milestone tracker template | Sections 4, 6, 7 and 8 |
| Development log template | The dated session record in [2026-11-11-aegis.md](../development-log/2026-11-11-aegis.md), with the evidence consolidated here |

The generic templates remain reusable portfolio resources. This AEGIS record is deliberately kept in ENGINEERING LAB; do not instantiate these templates in the AEGIS product repository for this portfolio-reporting task.

## 11. Change and update protocol

When another AEGIS work session is completed:

1. Do the implementation and product-level testing in the dedicated AEGIS workspace.
2. Bring the verified milestone, tested revision, exact outcomes and remaining issues back to ENGINEERING LAB.
3. Update this consolidated AEGIS record and the portfolio status/roadmap only where the evidence changes.
4. Add a dated portfolio development-log entry only for a meaningful session or milestone.
5. Keep completed evidence and outstanding checks separate.
6. Never claim a result that was not observed, and never copy secrets or credentials into portfolio documentation.

**Current portfolio decision:** Keep AEGIS **In Progress**. The next work is verification and operational hardening—not a rebuild and not a portfolio-driven redesign.
