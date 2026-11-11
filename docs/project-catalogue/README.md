# ENGINEERING LAB — Project Catalogue

This catalogue describes the intended products in ENGINEERING LAB. It is a planning and navigation document, not a claim that every project has been implemented.

Each product should remain independently understandable and independently deployable where appropriate. A separate repository should be created when a project moves from discovery into committed implementation and has a clear scope.

## Status key

- **Active:** implementation is underway.
- **Planned:** an identified future project; implementation has not started.
- **Discovery required:** the concept needs sharper boundaries or feasibility work before implementation.
- **Proposed integration:** a possible connection between products; not implemented unless separately verified.

## Priority overview

| Priority | Project | Status | Intended focus |
|---|---|---|---|
| 2 | SENTINEL QA | Planned — next major build | Automated quality engineering |
| 3 | MERIDIAN | Planned | Enterprise business and financial-services workflows |
| 4 | ORBIT | Planned | Visual low-code application and workflow builder |
| 5 | FORGE | Planned | Programming language and compiler foundations |
| 6 | NEXUS | Planned | Relational database internals |
| 7 | GITFORGE | Planned | Version-control internals |
| 8 | CHRONOS | Planned | Event streaming and messaging |
| 9 | OBSERVA | Planned | Observability and site reliability engineering |
| 10 | ATLAS | Planned | Distributed task execution and orchestration |
| 11 | NEBULA | Planned | Deployment and internal developer platform |
| 12 | CORTEX | Planned | Controlled multi-agent AI platform |
| 13 | ORACLE | Planned | Document knowledge and retrieval |
| 14 | SYNAPSE | Planned | Machine-learning lifecycle operations |
| 15 | Specialist systems | Planned | Computational, scientific, and systems projects |

Priority is a suggested sequence, not a deadline. Reassess it at milestone boundaries using prerequisites, learning value, available time, and maintenance cost.

---

## 1. SENTINEL QA — Quality Engineering Platform

<badge>Planned · next major build</badge>

**Purpose**

A reusable quality engineering platform demonstrating automated verification across APIs, browser interfaces, and performance workloads.

**Candidate technology**
- Java and Maven.
- Selenium for browser automation.
- JUnit or TestNG for test orchestration.
- REST Assured for API testing.
- JMeter for performance experiments.
- GitHub Actions for continuous integration.
- PostgreSQL only if test-run persistence or reporting needs justify it.

**Core engineering challenges**
- Maintainable test architecture and reusable fixtures.
- Test data setup, isolation, and cleanup.
- API assertions, schema checks, and negative testing.
- Browser automation reliability and diagnostics.
- Parallel execution and test categorisation.
- Useful reports, failure artefacts, and CI quality gates.
- Performance test design with controlled workloads.

**First milestone direction**

Create a small Java/Maven project with a clean test structure, configuration management, one representative API test suite, and repeatable local execution. Add CI after local execution is reliable.

**Proposed integration**


**Repository:** to be created after discovery and initial scope approval.

## 2. MERIDIAN — Enterprise Business and Financial Services Platform

<badge>Planned</badge>

**Purpose**

An enterprise application exploring reliable transactional workflows, role-based access, audit history, reporting, and data integrity. Use synthetic data and clearly label the system as an educational project; do not imply integration with real financial institutions.

**Candidate technology**
- C# and ASP.NET Core.
- Entity Framework Core.
- PostgreSQL or SQL Server.
- JavaScript or TypeScript frontend.
- xUnit.
- Docker for reproducible development and deployment.

**Core engineering challenges**
- Domain modelling and transactional boundaries.
- Authentication and fine-grained authorisation.
- Validation and consistent error handling.
- Database migrations and integrity constraints.
- Audit trails and reporting.
- Concurrency, idempotency, and failure recovery.

**Potential integration**

ORBIT could eventually submit approved workflows to MERIDIAN through a documented API. This is a future possibility, not an implemented connection.

**Repository:** to be created after discovery.

## 3. ORBIT — Visual Low-Code Application and Workflow Builder

<badge>Planned</badge>

**Purpose**

A visual environment for defining forms, business rules, approval flows, and application workflows without manually coding every routine step.

**Candidate technology**
- TypeScript or JavaScript.
- A modern component-based frontend framework if complexity warrants it.
- FastAPI or another justified service layer.
- PostgreSQL for definitions, versions, and workflow state.

**Core engineering challenges**
- Form and workflow definition schemas.
- Visual editor state and versioning.
- Validation and rule evaluation.
- Workflow state transitions and approvals.
- Permission boundaries and execution isolation.
- Import/export and integration adapters.

**Important design constraint**

User-authored rules and workflow definitions must be treated as untrusted input. Avoid arbitrary code execution. Define a constrained expression model and explicit execution permissions.

**Scope question**

FLOWSTATE may overlap with ORBIT. During discovery, decide whether durable process execution belongs inside ORBIT or warrants a separate engine.

**Repository:** to be created after discovery.

## 4. FLOWSTATE — Business Process Automation Engine

<badge color="warning">Discovery required</badge>

**Purpose**

Explore durable business process execution: stateful workflows, timers, retries, approvals, and recovery after service interruptions.

**Candidate technology**

Python or TypeScript, relational persistence, and a queue or event mechanism only where required.

**Core engineering challenges**
- Durable workflow state.
- Deterministic state transitions.
- Retry and timeout policies.
- Human approval steps.
- Idempotent task execution.
- Versioned workflow definitions and recovery.

**Boundary to resolve**

Determine whether FLOWSTATE should be a standalone execution engine or a subsystem of ORBIT. Do not build two overlapping products simply to increase the project count.

**Repository:** not yet justified; decide after discovery.

## 5. APEX — API Management and Integration Platform

<badge>Planned</badge>

**Purpose**

Explore API registration, gateway policies, authentication, rate limiting, versioning, analytics, and developer-facing API documentation.

**Candidate technology**

Go, Java, or Python selected after comparing gateway performance, concurrency, ecosystem, and learning objectives.

**Core engineering challenges**
- Request routing and policy evaluation.
- Authentication and authorisation.
- Rate limiting and quotas.
- API lifecycle and version management.
- Observability and audit records.
- Safe configuration reloads and failure behaviour.

**Repository:** to be created after discovery.

## 6. VERITAS — Security Governance and Policy Platform

<badge color="warning">Discovery required</badge>

**Purpose**

Potentially explore security governance, policy management, evidence tracking, and compliance workflows.

**Core engineering challenges**
- Policy representation and versioning.
- Ownership, approvals, and evidence history.
- Mapping controls to technical evidence.
- Access control and auditability.
- Clear distinction between policy status and verified technical state.

**Boundary to resolve**


**Repository:** not yet justified; decide after discovery.

## 7. QUANTUM TEST LAB — Distributed Performance and Reliability Testing

<badge>Planned</badge>

**Purpose**

A controlled workload platform for running repeatable performance, load, stress, and resilience experiments against authorised systems.

**Candidate technology**

A language and execution model selected after defining workload orchestration, worker coordination, and telemetry requirements.

**Core engineering challenges**
- Workload definition and scheduling.
- Coordinated distributed workers.
- Result aggregation and time-series analysis.
- Reproducible test environments.
- Rate limits and safeguards against unintended load.
- Fault injection in isolated, authorised environments.

**Repository:** to be created after discovery.

## 8. FORGE — Programming Language and Compiler

<badge>Planned</badge>

**Purpose**

Implement a small programming language to understand language design, parsing, execution, diagnostics, and compilation.

**Candidate technology**

Start in Python for iteration speed or choose Rust/C++ to deepen systems knowledge.

**Core engineering challenges**
- Grammar and lexical analysis.
- Parser and abstract syntax tree.
- Type checking and semantic analysis.
- Interpreter and runtime.
- Compiler intermediate representation.
- Diagnostics, source locations, and tests.

**Suggested first boundary**

A small expression language with variables, arithmetic, functions, and useful error messages. Expand only after the language core is reliable.

**Repository:** to be created after discovery.

## 9. NEXUS — Relational Database Engine

<badge>Planned</badge>

**Purpose**

Build a small relational database engine to understand storage, indexing, query execution, transactions, and recovery.

**Candidate technology**

Rust, C++, or Go, chosen based on the intended learning focus.

**Core engineering challenges**
- Page and record formats.
- Buffer management and persistence.
- B-tree or other index structures.
- SQL subset parsing and query planning.
- Transaction isolation and concurrency.
- Write-ahead logging and recovery.

**Suggested first boundary**

A durable key-value or record store with a documented file format and tests before adding SQL and transactions.

**Repository:** to be created after discovery.

## 10. GITFORGE — Version Control Engine

<badge>Planned</badge>

**Purpose**

Implement the core concepts behind version control to understand content-addressed storage, snapshots, history, and branching.

**Candidate technology**

Go, Rust, or Python for an initial educational implementation.

**Core engineering challenges**
- Object hashing and storage.
- Trees, blobs, and commit metadata.
- References and history traversal.
- Diff generation.
- Branching and merge concepts.
- Integrity checks and repository recovery.

**Suggested first boundary**

A local command-line tool that stores file snapshots and can inspect history. Do not attempt full compatibility with Git as the first milestone.

**Repository:** to be created after discovery.

## 11. SENTINEL CODE — Static Analysis and Code Quality

<badge>Planned</badge>

**Purpose**

Analyse source code and report configurable correctness, maintainability, and security-oriented findings.

**Candidate technology**

Python or TypeScript initially, with language-specific parsers selected for the supported targets.

**Core engineering challenges**
- Parsing and syntax-tree traversal.
- Rule definitions and configuration.
- Diagnostics with source locations.
- Severity and suppression handling.
- False-positive management.
- CI integration and machine-readable output.

**Repository:** to be created after discovery.

## 12. CHRONOS — Event Streaming Platform

<badge>Planned</badge>

**Purpose**

Explore durable event logs, producers, consumers, partitions, offsets, and delivery guarantees.

**Candidate technology**

Go or Java.

**Core engineering challenges**
- Append-only log storage.
- Partitioning and consumer offsets.
- Delivery and ordering semantics.
- Backpressure and flow control.
- Retention and replay.
- Failure recovery and observability.

**Potential integration**


**Repository:** to be created after discovery.

## 13. OBSERVA — Observability and SRE Platform

<badge>Planned</badge>

**Purpose**

Collect and interpret metrics, logs, and traces to help understand service health and reliability.

**Candidate technology**

OpenTelemetry-compatible instrumentation and collectors, with storage and visualisation choices made after a small prototype.

**Core engineering challenges**
- Instrumentation and context propagation.
- Metrics, logs, and traces.
- Service-level indicators and objectives.
- Alert design and noise reduction.
- Retention, cardinality, and data costs.
- Incident timelines and operational runbooks.

**Repository:** to be created after discovery.

## 14. ATLAS — Distributed Computing and Orchestration

<badge>Planned</badge>

**Purpose**

Explore scheduling and coordinating work across independent workers.

**Candidate technology**

Go or Python, with a relational store and message transport selected according to delivery requirements.

**Core engineering challenges**
- Task scheduling and worker registration.
- Distributed task state.
- Retry, timeout, and cancellation semantics.
- Idempotency and duplicate execution.
- Worker health and recovery.
- Fairness and resource limits.

**Repository:** to be created after discovery.

## 15. NEBULA — Cloud Deployment and Developer Platform

<badge>Planned</badge>

**Purpose**

Explore repeatable deployment, environment configuration, service templates, and internal developer workflows.

**Candidate technology**

Docker, infrastructure automation, CI/CD, and Kubernetes only when the project scope genuinely requires orchestration.

**Core engineering challenges**
- Reproducible environments.
- Deployment and rollback.
- Secrets and configuration.
- Policy and access control.
- Service templates and developer experience.
- Deployment observability and cost awareness.

**Potential integration**

NEBULA may deploy selected portfolio products once their deployment requirements are documented.

**Repository:** to be created after discovery.

## 16. CORTEX — Multi-Agent AI Platform

<badge>Planned</badge>

**Purpose**

Explore coordinated AI agents with bounded tools, explicit permissions, evaluation, and traceable actions.

**Candidate technology**

Python, model/provider adapters, structured tool interfaces, and an evaluation framework.

**Core engineering challenges**
- Agent orchestration and state.
- Tool permissions and least privilege.
- Human approval for consequential actions.
- Evaluation and reproducibility.
- Prompt-injection and untrusted-input handling.
- Tracing, cost, latency, and failure management.

**Repository:** to be created after discovery.

## 17. ORACLE — Document Knowledge and Retrieval Platform

<badge>Planned</badge>

**Purpose**

Build a document ingestion and retrieval system that answers questions with traceable references to authorised source material.

**Candidate technology**

Python, document parsers, search infrastructure, optional vector retrieval, and relational metadata storage.

**Core engineering challenges**
- Document ingestion and extraction quality.
- Chunking and metadata.
- Hybrid search and retrieval evaluation.
- Source citations and provenance.
- Access-aware retrieval.
- Data deletion, versioning, and re-indexing.

**Repository:** to be created after discovery.

## 18. SYNAPSE — MLOps Platform

<badge>Planned</badge>

**Purpose**

Explore the lifecycle of machine-learning experiments, datasets, models, evaluation, deployment, and monitoring.

**Candidate technology**

Python and carefully selected experiment-tracking, model-packaging, and serving tools.

**Core engineering challenges**
- Dataset and experiment versioning.
- Reproducible training.
- Model evaluation and comparison.
- Model registry and deployment.
- Drift and performance monitoring.
- Rollback and lineage.

**Repository:** to be created after discovery.

## 19. PHOENIX — Educational Operating System and Kernel

<badge>Planned</badge>

**Purpose**

Explore operating-system fundamentals through a small educational kernel in a controlled emulator.

**Candidate technology**

C or Rust, assembly where necessary, and an emulator such as QEMU.

**Core engineering challenges**
- Boot sequence and kernel entry.
- Memory layout and allocation.
- Interrupts and exceptions.
- Scheduling and context switching.
- Basic device interaction.
- Filesystem and process concepts.

**Safety boundary**

Start in an emulator. Do not experiment on the user's primary device or physical hardware without a carefully reviewed recovery plan.

**Repository:** to be created after discovery.

## 20. VELOCITY — High-Performance Computing and Simulation

<badge>Planned</badge>

**Purpose**

Explore numerical simulation, parallel computation, and performance engineering.

**Candidate technology**

C++, Rust, or Python with native numerical libraries depending on the problem.

**Core engineering challenges**
- Numerical methods and error analysis.
- Data layout and memory locality.
- Parallel algorithms.
- Profiling and optimisation.
- Reproducible benchmarks.
- Validation against analytical or reference solutions.

**Repository:** to be created after discovery.

## 21. HELIOS — Energy Management and Optimisation

<badge>Planned</badge>

**Purpose**

Model energy use and explore optimisation of consumption, storage, and demand under explicit constraints.

**Candidate technology**

Python, optimisation libraries, time-series processing, and a web interface if it adds value.

**Core engineering challenges**
- Energy data modelling and quality.
- Forecasting uncertainty.
- Constraint-based optimisation.
- Scenario analysis.
- Explainability of recommendations.
- Validation against known or simulated cases.

**Repository:** to be created after discovery.

## 22. AURORA — Digital Twin and Simulation Platform

<badge>Planned</badge>

**Purpose**

Represent a real or simulated system digitally, track its state, and explore scenarios without claiming that a model perfectly reproduces reality.

**Candidate technology**

Selected after choosing a bounded domain and fidelity target; may combine simulation code, data pipelines, and visualisation.

**Core engineering challenges**
- Domain model and state representation.
- Synchronisation and event history.
- Model calibration and validation.
- Uncertainty and sensitivity analysis.
- Scenario execution and comparison.
- Clear distinction between observed and simulated values.

**Repository:** to be created after discovery.

## 23. POLARIS — Geospatial Intelligence Platform

<badge>Planned</badge>

**Purpose**

Explore spatial data processing, geospatial querying, analysis, and map-based visualisation.

**Candidate technology**

Python, PostgreSQL/PostGIS, geospatial libraries, and a web mapping interface.

**Core engineering challenges**
- Coordinate reference systems.
- Spatial indexing and queries.
- Geospatial data ingestion and validation.
- Raster and vector processing.
- Spatial analysis and uncertainty.
- Map performance and accessible visualisation.

**Repository:** to be created after discovery.

## 24. QUANTUM — Quantum Computing Simulator

<badge>Planned</badge>

**Purpose**

Build an educational simulator for quantum circuits and understand the mathematics behind quantum state evolution.

**Candidate technology**

Python with numerical linear algebra; consider a lower-level implementation only when profiling justifies it.

**Core engineering challenges**
- Complex state vectors.
- Quantum gates and tensor products.
- Measurement and probability.
- Circuit representation and simulation.
- Numerical correctness and test cases.
- Exponential memory and compute limits.

**Repository:** to be created after discovery.

---

## Shared expectations for every flagship

Before a project is treated as a serious portfolio deliverable, it should have, where applicable:

- A clear problem statement, intended users, scope, and non-goals.
- Architecture documentation and recorded significant decisions.
- A maintainable source layout and reproducible development setup.
- Explicit data ownership, validation, and migration strategy.
- Documented APIs or other integration contracts.
- Authentication, authorisation, and safe secret handling where required.
- Automated tests, CI checks, and quality gates.
- Security, dependency, and accessibility considerations.
- Error handling, logging, and operational guidance.
- A reproducible demonstration, known limitations, and evidence for claims.

Not every prototype needs enterprise infrastructure. The standard is to make scope explicit and add complexity only when the requirements justify it.

## Catalogue maintenance

When a project moves into discovery:
1. Write its problem statement and intended users.
2. Define scope, non-goals, risks, and acceptance criteria.
3. Compare candidate technologies against the requirements.
4. Decide whether it deserves a separate repository.
5. Record major decisions in the portfolio's decision log.

When implementation begins, add its repository link and update the status here and in ROADMAP.md. Keep both documents consistent.

**Guiding principle:** each project must teach or demonstrate a distinct engineering capability. If two projects do the same job, consolidate or differentiate them before investing in both.
