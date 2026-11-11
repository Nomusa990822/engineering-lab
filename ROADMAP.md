# ENGINEERING LAB — Portfolio Roadmap

**Portfolio:** ENGINEERING LAB  
**Tagline:** SOFTWARE · SYSTEMS · INTELLIGENCE · RESEARCH  
**Roadmap type:** Living strategy and delivery plan  
**Last updated:** 11 November 2026

---

## 1. Purpose

This roadmap describes the intended evolution of ENGINEERING LAB: a portfolio of independent, technically substantial software products supported by shared engineering standards, documented interfaces, and a portfolio hub.

It is a prioritised direction, not a commitment to build every listed project. The objective is to demonstrate engineering depth through a small number of excellent, tested, explainable products rather than accumulate many unfinished repositories.

The roadmap changes when evidence, learning, technical constraints, or project value justify a change. Completion is determined by acceptance criteria, not by calendar dates.

## 2. Current portfolio position

| Item | Status | Evidence and qualification |
|---|---|---|
| ENGINEERING LAB hub | In Progress | Repository exists; core design, standards, architecture, and integration documents have been established |
| AEGIS Security Platform | In Progress | Existing FastAPI-based educational security platform; 10–11 November checkpoint records container hardening, persistence and database checks, selected API authorization outcomes, dashboard verification, and five successful latest CI workflows; outstanding operational checks remain |
| SENTINEL QA | Planned | Intended next major product; not yet implemented |
| All other catalogue projects | Planned | Concepts for future discovery; not yet implemented |

A status must reflect verified repository evidence. A document describing a future capability does not mean that capability has been built.

## 3. Delivery principles

1. **Depth over quantity.** Prioritise three to five flagship products for substantial implementation and validation.
2. **Preserve working systems.** Improve AEGIS without casually replacing working features or forcing it into another product's architecture.
3. **Build in vertical slices.** Each milestone should produce a working, testable increment.
4. **Make quality visible.** Tests, security checks, architecture decisions, reproducible demonstrations, and honest limitations are part of the product.
5. **Integrate through contracts.** Use documented APIs, events, or other explicit interfaces; do not couple independent products through shared database tables.
6. **Choose technology for a reason.** A technology belongs in a project only when its capabilities serve a clear requirement.
7. **Measure before claiming.** Performance, coverage, reliability, and security claims require repeatable evidence.
8. **Keep scope sustainable.** The indicative study/build budget is five to eight focused hours per week, adjusted around energy and other commitments.

## 4. Priority sequence

### Phase 0 — Establish the portfolio hub

**Objective:** Make ENGINEERING LAB understandable, navigable, and governed before expanding the product catalogue.

**Work items**
- Complete the core portfolio documents.
- Create a clear repository README as the front door.
- Create a project catalogue with each project's purpose, status, and repository link when one exists.
- Add architecture decision records as consequential decisions are made.
- Keep the roadmap and project statuses current.

**Exit criteria**
- A new reader can understand the portfolio, its architecture, current status, and intended direction.
- Planned work is visibly distinguished from implemented work.
- Existing product repositories remain independent.

### Phase 1 — AEGIS baseline and SENTINEL QA

**Objective:** Preserve AEGIS as the existing flagship while building a credible enterprise-grade QA automation platform.

**AEGIS baseline**
- Record the current working state and how to run it. **Checkpoint recorded 11 November 2026** in [the ENGINEERING LAB development log](docs/development-log/2026-11-11-aegis.md).
- A 10–11 November verification checkpoint has been recorded: hardened container configuration, persistent SQLite data after restart, SQLite integrity and foreign-key checks, dependency consistency, selected API role outcomes, dashboard rendering, and five successful latest CI workflows.
- Remaining verification: Codespaces port visibility, complete route-specific authorization matrix, local full-suite results from the current working tree, working-tree reconciliation, and backup/restore exercise.
- Continue implementation and detailed product-level documentation in the independent AEGIS repository and its dedicated development conversation. ENGINEERING LAB records only portfolio status, milestones, and cross-project decisions.
- Record known limitations and avoid unverified claims.
- Do not redesign its visual identity as part of the shared portfolio work.

**SENTINEL QA**
- Candidate stack: Java, Maven, Selenium, JUnit or TestNG, REST Assured, PostgreSQL where persistence is justified, JMeter, Docker, and GitHub Actions.
- Begin with a maintainable test automation framework and a small representative application/API test suite.
- Add browser automation, API contract checks, test data management, reporting, and performance testing in deliberate increments.
- Make test execution reproducible locally and in CI.

**First integration candidate**
- SENTINEL QA may test AEGIS through its documented public API and supported test environment.
- This is a proposed integration. It must not depend on AEGIS's internal database.
- Establish test accounts, safe test data, environment isolation, cleanup, and explicit limits before running automated tests against AEGIS.

**Exit criteria**
- AEGIS baseline is documented and key workflows have repeatable verification.
- SENTINEL QA has a documented architecture, runnable test framework, meaningful automated tests, CI execution, and readable reports.
- Any AEGIS integration uses a documented contract and has integration tests.

### Phase 2 — Enterprise application engineering

**Objective:** Demonstrate robust business application design, workflow modelling, and maintainable full-stack delivery.

**MERIDIAN — Enterprise financial/services management**
- Candidate stack: C#/.NET, ASP.NET Core, Entity Framework Core, PostgreSQL or SQL Server, JavaScript/TypeScript, Redis or RabbitMQ only where justified, Docker, and xUnit.
- Explore secure identity and role-based access, transactional workflows, audit history, reporting, validation, and reliable data handling.
- Use synthetic data; do not imply connection to real financial institutions.

**ORBIT — Visual low-code workflow and application builder**
- Candidate stack: TypeScript/JavaScript, a modern web UI framework if needed, FastAPI or another justified service layer, and PostgreSQL.
- Explore form design, workflow definition, validation rules, approvals, versioning, and integration adapters.
- Treat user-authored workflows as untrusted input and design execution boundaries carefully.

**FLOWSTATE — Business process automation engine**
- Candidate stack selected after discovery; likely TypeScript or Python with durable workflow state.
- Consider whether its capabilities should instead become a focused subsystem of ORBIT. Avoid building overlapping products without a clear distinction.

**APEX — API management and integration platform**
- Candidate stack: Go, Java, or Python depending on the gateway and control-plane requirements.
- Explore API registration, policy enforcement, authentication, rate limits, analytics, and developer experience.

**VERITAS — Security and governance platform**
- Discover the precise problem and boundary before selecting a stack.
- Avoid duplicating AEGIS; focus on a clearly differentiated governance, policy, or compliance workflow if justified.

**Exit criteria**
- At least one enterprise application has a complete vertical slice from user interface through validated business logic and persistent data.
- Authentication, authorisation, auditability, migrations, automated tests, and deployment are demonstrated where applicable.
- Product boundaries are clear enough to justify separate repositories.

### Phase 3 — Computer science foundations

**Objective:** Build lower-level understanding by implementing core computing concepts rather than only integrating existing frameworks.

| Project | Focus | Candidate implementation |
|---|---|---|
| FORGE | Programming language, parser, interpreter or compiler | Start with a small grammar, lexer, parser, AST, diagnostics, and interpreter; add compilation later |
| NEXUS | Relational database engine | Storage pages, records, indexes, query parsing/planning, transactions, and recovery in staged scope |
| GITFORGE | Version-control engine | Content-addressed objects, snapshots, references, commits, diffs, and branching concepts |
| SENTINEL CODE | Static analysis and code-quality tool | Parsing, rule engine, diagnostics, configuration, and CI integration |

**Exit criteria**
- Each selected project has a written scope and architecture.
- Core algorithms and data structures are implemented and tested, not merely wrapped around an existing product.
- Correctness tests include edge cases and documented limitations.
- Performance comparisons are published only when measured using repeatable workloads.

### Phase 4 — Distributed systems and infrastructure

**Objective:** Understand service coordination, event processing, deployment, and production operations.

| Project | Focus | Candidate technologies |
|---|---|---|
| CHRONOS | Event streaming platform | Go or Java; append-only logs, partitions, consumer offsets, delivery semantics |
| OBSERVA | Observability and SRE platform | OpenTelemetry concepts, metrics, logs, traces, alerting, service-level indicators |
| ATLAS | Distributed computing and orchestration | Go or Python; scheduling, workers, task state, retries, and coordination |
| NEBULA | Cloud deployment and internal developer platform | Containers, infrastructure automation, deployment workflows, policy and service templates |
| QUANTUM TEST LAB | Distributed performance and reliability testing | Workload generation, coordinated runners, telemetry, fault injection in controlled environments |

Build only the infrastructure needed to prove the core engineering ideas. Kubernetes, brokers, and distributed deployment are not prerequisites for every early milestone.

**Exit criteria**
- Failure modes and recovery behaviour are explicitly tested.
- Service boundaries, delivery guarantees, retry policies, and operational signals are documented.
- A reproducible deployment and useful operational runbook exist for the chosen flagship.

### Phase 5 — AI and data platforms

**Objective:** Build AI systems with explicit evaluation, safety boundaries, data provenance, and operational controls.

| Project | Focus | Candidate technologies |
|---|---|---|
| CORTEX | Multi-agent AI platform | Python, tool interfaces, orchestration, permissions, evaluation |
| ORACLE | Document knowledge and retrieval platform | Python, ingestion pipelines, search, vector retrieval, citations and access controls |
| SYNAPSE | MLOps platform | Python, experiment tracking, model evaluation, versioning, deployment and monitoring |

**Exit criteria**
- Evaluation datasets and metrics are documented.
- Outputs can be traced to relevant inputs or sources where applicable.
- Permissions, data handling, failure behaviour, and human oversight are designed explicitly.
- Model quality and latency claims are supported by measured experiments.

### Phase 6 — Computational and specialist systems

**Objective:** Pursue specialist projects after the required mathematical, systems, and domain foundations are in place.

| Project | Focus | Discovery considerations |
|---|---|---|
| VELOCITY | High-performance computing and simulation | Numerical methods, parallelism, profiling, correctness |
| HELIOS | Energy management and optimisation | Energy-system models, constraints, optimisation and real-world data quality |
| AURORA | Digital twin and simulation platform | Model fidelity, state synchronisation, uncertainty and validation |
| POLARIS | Geospatial intelligence and spatial analytics | Coordinate systems, spatial indexes, geospatial data and visualisation |
| QUANTUM | Quantum computing simulator | Linear algebra, complex amplitudes, gates, measurement and simulation limits |
| PHOENIX | Educational operating system/kernel | C or Rust, boot process, memory, interrupts, scheduling and safe hardware experimentation |

**Exit criteria**
- Domain assumptions and mathematical foundations are documented.
- Results are validated against known examples or reference implementations.
- Simulation limitations and numerical error are reported honestly.

## 5. Project catalogue and current status

The catalogue below is a planning inventory, not a declaration that these products exist.

| Project | Intended domain | Current status |
|---|---|---|
| AEGIS | Cybersecurity detection and response | In Progress |
| SENTINEL QA | Quality engineering and test automation | Planned — next major build |
| MERIDIAN | Enterprise business/financial services software | Planned |
| ORBIT | Low-code workflow and application builder | Planned |
| FLOWSTATE | Business process automation | Planned; scope to be compared with ORBIT |
| APEX | API management and integration | Planned |
| VERITAS | Security governance and policy | Planned; differentiation required |
| QUANTUM TEST LAB | Distributed performance/reliability testing | Planned |
| ATLAS | Distributed computing and orchestration | Planned |
| FORGE | Programming language/compiler | Planned |
| NEXUS | Relational database engine | Planned |
| NEBULA | Cloud and developer platform | Planned |
| CHRONOS | Event streaming | Planned |
| CORTEX | Multi-agent AI | Planned |
| ORACLE | Document knowledge and retrieval | Planned |
| SYNAPSE | MLOps | Planned |
| PHOENIX | Educational operating system/kernel | Planned |
| VELOCITY | HPC and simulation | Planned |
| SENTINEL CODE | Static analysis and code quality | Planned |
| GITFORGE | Version control engine | Planned |
| OBSERVA | Observability and SRE | Planned |
| POLARIS | Geospatial analytics | Planned |
| HELIOS | Energy management and optimisation | Planned |
| QUANTUM | Quantum computing simulator | Planned |
| AURORA | Digital twin and simulation | Planned |

A project moves from Planned to Discovery when investigation begins, and to In Progress when implementation work is underway. Use the shared portfolio status vocabulary defined below and in [docs/PROJECT-STATUS.md](docs/PROJECT-STATUS.md).

## 6. Project lifecycle and status definitions

Use the same status vocabulary as the portfolio dashboard:

- **Proposed:** An idea under consideration; not yet selected.
- **Planned:** Selected for future work, but implementation has not started.
- **Discovery:** Requirements, risks, feasibility, users, and technical options are being investigated.
- **In Progress:** Implementation is underway against an agreed milestone.
- **In Review:** A defined change is awaiting review or acceptance.
- **Blocked:** Progress depends on an identified unresolved issue.
- **Complete:** A specifically defined milestone meets its acceptance criteria; this does not imply the entire product is complete.
- **Maintained:** The product is in a stable maintenance mode with ongoing support.
- **Paused:** Work is intentionally stopped; record the reason and restart condition.
- **Archived:** Work is retired and no longer actively maintained.

A status applies only to the scope and version actually verified. A working local prototype is not automatically production-ready. A release may be recorded in the project's release history without creating a separate portfolio status category.

### Milestone gate

Before implementation:
- Define the problem and intended user.
- Set explicit in-scope and out-of-scope boundaries.
- Record architecture and data decisions.
- Identify security, privacy, accessibility, and operational risks.
- Define acceptance criteria and a demonstration.

Before calling a milestone complete:
- Run the relevant automated tests.
- Verify the main user or system workflow.
- Review failure and edge cases.
- Check documentation and setup instructions.
- Record evidence, limitations, and the next decision.

## 7. Working rhythm

The indicative target is five to eight focused hours per week. It is a guide, not a penalty or deadline.

A flexible weekly rhythm:
- **Planning/review:** choose one milestone and define its acceptance criteria.
- **Learning/design:** study the concepts needed and record design decisions.
- **Implementation:** build one coherent vertical slice.
- **Verification:** run tests, inspect failures, and validate behaviour.
- **Documentation:** update the README, architecture notes, and progress record.

Sessions may be moved, shortened, or skipped when necessary. Do not advance a milestone merely because a planned session has passed.

A weekly engineering build programme is scheduled for Mondays at 18:00 Africa/Johannesburg, beginning 16 November 2026. This is a planning automation, not a claim that a Google Calendar event has been created.

## 8. Integration direction

Potential integrations are governed by INTEGRATION-STRATEGY.md and ARCHITECTURE.md. Examples include:
- SENTINEL QA testing AEGIS through documented APIs.
- AEGIS publishing selected security events to CHRONOS.
- CHRONOS exposing event streams to OBSERVA.
- NEBULA deploying selected independent products.
- ORACLE indexing approved project documentation.
- CORTEX assisting with bounded analysis under explicit permissions.

These are proposals only. They must not be represented as implemented until the interfaces, security controls, tests, and operational behaviour have been built and verified.

## 9. Roadmap governance

Review priorities at milestone boundaries and during weekly planning. Reorder or remove projects when:
- A project duplicates another project's purpose.
- A prerequisite is missing.
- The technical cost is disproportionate to the learning or portfolio value.
- A smaller project or vertical slice would demonstrate the concept more clearly.
- Quality or maintenance of an existing flagship would suffer.

Keep a short record of material changes in docs/decisions. Update this roadmap when priorities or scope change, and update project status only after verification.

## 10. Immediate next actions

1. Review the portfolio documentation and tracking system for consistency.
2. Verify the AEGIS repository baseline, including run instructions, tests, and current known limitations.
3. Start SENTINEL QA discovery: problem statement, scope, architecture, toolchain, and first acceptance criteria.
4. Build the first SENTINEL QA vertical slice only after its design is reviewed.

**Guiding rule:** build fewer systems, understand them deeply, verify them rigorously, and explain them clearly.
