# Engineering Standards

**Portfolio:** ENGINEERING LAB  
**Scope:** All independent ENGINEERING LAB repositories  
**Status:** Active standard; apply proportionately to each project's maturity and risk.

## 1. Purpose

These standards define a shared quality baseline for software developed under ENGINEERING LAB. The portfolio is a collection of independent products, not a monolith. Each product owns its code, configuration, tests, documentation, data lifecycle and release process. Shared standards do not require identical languages, frameworks or repository layouts.

A prototype may be intentionally limited, but its maturity and limitations must be stated honestly. Do not imply production readiness without evidence.

## 2. Engineering principles

- Correctness and user outcomes come before novelty or visual polish.
- Prefer readable, maintainable designs over cleverness and unnecessary abstraction.
- Build security, privacy and failure handling into design decisions.
- Design important behaviour to be testable and observable.
- Define explicit interfaces between modules and services.
- Make builds, tests and demonstrations reproducible.
- Design accessible interfaces and document consequential decisions.
- Choose technology to satisfy requirements, not to maximise the technology list.
- Support technical claims with repeatable evidence.

## 3. Project lifecycle

For meaningful work, follow: **Frame the problem → Define requirements → Design → Implement → Verify → Review → Release → Operate and learn.**

Requirements should include acceptance criteria and relevant non-functional needs such as security, performance, accessibility, reliability and maintainability. Keep the process lightweight for small changes, but do not skip design or verification for high-risk work.

## 4. Repository structure

Use a structure suited to the language and framework. A typical project separates application source, tests, migrations, scripts, configuration examples and documentation. Keep responsibilities clear and entry points discoverable.

Do not commit credentials, private keys, local environments, caches, private user data or generated noise. The README must explain prerequisites, setup, configuration, run commands, test commands and current limitations.

## 5. Coding standards

### Readability
- Follow established language and framework conventions.
- Use formatters, linters and static analysis where practical.
- Choose descriptive names and focused functions/modules.
- Prefer explicit dependencies and simple control flow.
- Remove dead code and temporary debugging output.
- Comment on intent, constraints and non-obvious reasoning.

### Types, validation and errors
- Use types, schemas or explicit interfaces where supported and useful.
- Validate untrusted input at system boundaries: APIs, files, environment variables and messages.
- Document public interfaces and their failure behaviour.
- Handle expected errors explicitly; do not silently swallow exceptions.
- Return safe, actionable errors without exposing internals.

### Configuration and dependencies
- Keep environment-specific configuration outside source code.
- Provide an example configuration file with placeholders only.
- Never commit secrets or hardcode credentials.
- Prefer maintained dependencies and commit the ecosystem's lockfile.
- Remove unused dependencies and review upgrades for security, licensing and compatibility.

## 6. Architecture and data

- Separate presentation, application, domain and infrastructure concerns where complexity warrants it.
- Keep dependency direction understandable and avoid circular dependencies.
- Prefer documented APIs, events or explicit contracts between independent products.
- Never use direct access to another product's database as an integration shortcut.
- Version public APIs and event schemas when compatibility matters.
- Use database constraints and transactions to protect integrity.
- Manage schema changes through repeatable migrations.
- Consider idempotency, retries, ordering and duplicate delivery in asynchronous workflows.
- Define retention, deletion, backup and recovery expectations for important data.
- Introduce microservices, queues, caches and orchestration only when justified.

## 7. Testing strategy

Use an appropriate mix of:

- **Unit tests** for isolated logic.
- **Integration tests** for databases, filesystems, queues and external dependencies.
- **Contract tests** for API and event compatibility.
- **End-to-end tests** for important user journeys.
- **Performance tests** for latency, throughput and resource use.
- **Security tests** for access control, abuse cases and relevant vulnerability classes.

Tests must assert meaningful outcomes, cover important boundary and failure cases, use safe reproducible data, and avoid dependence on uncontrolled external services. Fix flaky tests or document a temporary mitigation and owner. Coverage is a diagnostic, not proof of quality; never fabricate or inflate coverage figures.

Every repository must document how to run its tests and which checks are required before merge.

## 8. Security baseline

Apply controls proportionate to the system's data and exposure:

- Identify sensitive assets, trust boundaries and abuse cases.
- Authenticate users where identity is required and authorize every protected operation.
- Apply least privilege to users, services, tokens and database accounts.
- Validate untrusted input, encode output safely and use parameterized queries.
- Protect secrets with appropriate environment-specific secret management; rotate exposed credentials.
- Use secure transport for network communication beyond isolated local development.
- Configure secure session and cookie attributes when sessions are used.
- Apply suitable security headers to web applications.
- Avoid exposing stack traces, secrets, personal data or infrastructure details.
- Redact credentials and unnecessary sensitive data from logs.
- Scan dependencies and container images where relevant; investigate findings.
- Back up important data and verify restoration.
- Provide a responsible vulnerability-reporting route for projects exposed to external users.

Use recognised guidance such as OWASP resources where relevant. A passing scanner or checklist is not proof that a system is secure; state the scope and limitations of security evidence.

## 9. Quality gates and code review

A typical CI pipeline should install from the lockfile and run applicable formatting checks, linting, static/type analysis, unit and integration tests, build verification, dependency/secret scans and container/infrastructure checks where relevant.

Pull requests should explain the problem, solution, design decisions, tests, risks and configuration or migration impact. Review for correctness, clarity, security, compatibility, maintainability and documentation. Keep changes reviewable. Do not merge failing required checks without a documented exception and follow-up plan.

Enable branch protection and required checks when repository settings support them.

## 10. Git and release workflow

- Track meaningful work with issues or an equivalent task record.
- Use focused branches for features, fixes and maintenance.
- Keep commits scoped and write messages that explain the change.
- Use pull requests when review or a decision record is valuable.
- Tag intentional releases and maintain release notes or a changelog.
- Use Semantic Versioning for versioned products/APIs where appropriate: major for incompatible changes, minor for compatible features, patch for compatible fixes.
- Document breaking changes and migration steps.

A commit on the default branch is not automatically a release; a release tag is not proof of production readiness.

## 11. Documentation

Each repository should document:

- purpose, intended users and current maturity;
- capabilities and known limitations;
- architecture and important design decisions;
- prerequisites, setup and configuration;
- commands to run, test, build and inspect the system;
- API usage and examples where applicable;
- deployment and operational guidance where applicable;
- issue and security-reporting routes where applicable;
- screenshots, sample output or reproducible demonstrations when useful.

Maintain architecture documentation and Architecture Decision Records (ADRs) for consequential decisions. Update documentation alongside behaviour changes.

## 12. Observability

For services and long-running applications, provide diagnostics appropriate to complexity: structured logs, useful timestamps and severity, correlation identifiers where useful, actionable error context, health/readiness checks, and metrics for important behaviour. Add distributed tracing when multi-service paths justify it.

Do not log secrets, full request bodies by default or unnecessary personal data. Diagnostics should help distinguish application defects, configuration errors, dependency failures and infrastructure problems.

## 13. Deployment and operations

- Make builds and runtime configuration reproducible.
- Separate development, test and production configuration.
- Use containers when they improve consistency or portability.
- Document deployment prerequisites, ports, volumes, permissions and dependencies.
- Apply migrations through a controlled process.
- Define backup and restore procedures for important persistent data.
- Have a rollback or recovery approach for releases that can affect users or data.
- Monitor deployed services and document common failure diagnosis.
- Never expose development credentials, debug mode or permissive defaults publicly.

For local educational prototypes, state that scope clearly and explain what would be needed before real deployment.

## 14. UI quality and accessibility

For user-facing applications:
- support keyboard navigation and visible focus;
- use semantic markup and accessible names;
- associate form labels with inputs and explain validation errors;
- never communicate status by colour alone;
- maintain readable contrast in every supported theme;
- respect reduced-motion preferences;
- support narrow and wide viewports;
- provide loading, empty, success and error states;
- use consistent interaction patterns.

Accessibility is part of implementation, not merely a final visual check.

## 15. Performance and reliability evidence

Establish a baseline before claiming an optimisation. Record hardware, software, dataset, workload and commands used for benchmarks. Report relevant percentiles and resource use where appropriate, not only averages. Test realistic workloads and failure scenarios.

For networked systems, consider timeouts, bounded retries, back-pressure, graceful degradation and duplicate requests. Avoid retry storms and unbounded queues. Distinguish measured results from estimates and design targets.

Do not claim "production-grade", "enterprise-ready", "highly scalable" or a specific performance improvement without evidence and a stated scope.

## 16. Definition of Ready

A task is ready when:
- the problem and intended outcome are understood;
- acceptance criteria are verifiable;
- constraints and dependencies are identified;
- significant design and security questions have been considered;
- the task is appropriately scoped.

## 17. Definition of Done

A task is done when:
- acceptance criteria are met;
- implementation follows project conventions;
- relevant tests and quality checks pass;
- security and failure paths have been considered;
- documentation and configuration examples are updated;
- known critical regressions are resolved or explicitly recorded;
- the result has been reviewed or otherwise verified;
- claims about the result match the evidence.

A feature is not done merely because it worked once on a developer's machine.

## 18. Project maturity and honest status

Use clear maturity labels:

- **Prototype:** explores an idea; important behaviour or safeguards may be incomplete.
- **Functional:** documented core workflows work in the stated environment.
- **Validated:** important behaviour has repeatable tests and documented verification.
- **Release candidate:** release checks, documentation, security review and operational preparation are complete for the stated scope.
- **Released:** an intentional version is published with limitations and support expectations documented.

Always distinguish planned, in-progress, implemented and verified capabilities. Screenshots, passing CI, scan results and benchmark claims must be genuine outputs from the relevant version.

## 19. Exceptions and continuous improvement

These standards are a shared baseline, not a mandate for unnecessary process. A project may deviate when a requirement is irrelevant, a tool is unavailable or a simpler approach is more appropriate.

Document material exceptions with the requirement varied, reason, risks, compensating controls and review condition/date if temporary. Update this standard as the portfolio gains experience.

---

**Practical rule:** Understand → Design → Implement → Test → Review → Document → Release → Learn.

The goal is not identical repositories. The goal is for every ENGINEERING LAB project to be understandable, verifiable, responsible and worthy of technical scrutiny.
