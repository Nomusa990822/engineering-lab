# ADR-0001: Keep portfolio products in independent repositories

- **Status:** Accepted
- **Date:** 2026-11-10
- **Decision owners:** ENGINEERING LAB
- **Related:** [ARCHITECTURE.md](../../ARCHITECTURE.md), [INTEGRATION-STRATEGY.md](../../INTEGRATION-STRATEGY.md), [ROADMAP.md](../../ROADMAP.md)

## Context

ENGINEERING LAB contains multiple products with different problem domains, technology choices, data models, release cycles, and operational requirements. A single monorepo could make shared changes convenient, but it would also introduce coordination and tooling constraints across otherwise independent systems.

The portfolio needs a central place to describe shared principles without making every product depend on the same runtime, database, or release process.

## Decision drivers

- Preserve product autonomy and clear ownership.
- Allow each product to choose appropriate technologies.
- Keep builds, tests, issues, and releases independently manageable.
- Avoid accidental coupling through shared internal data.
- Retain a central portfolio-level overview and standards.

## Options considered

### Option A — One monorepo for all products

Advantages:
- One place for all source code.
- Cross-project changes can be coordinated in one commit.
- Some tooling and dependency conventions can be shared.

Disadvantages:
- Different languages and build systems increase repository complexity.
- Independent releases and access boundaries become harder to manage.
- Shared changes can create unnecessary coupling.

### Option B — Independent product repositories with a portfolio hub

Advantages:
- Products own their code, data, tests, and release lifecycle.
- Technology choices remain specific to each problem.
- The hub can document standards and link to products without controlling their internals.

Disadvantages:
- Cross-repository changes require explicit coordination.
- Shared conventions need documentation and occasional duplication.
- Portfolio-wide status must be maintained deliberately.

### Option C — Defer repository structure

This would delay the decision, but the portfolio repository already exists and the product boundaries are sufficiently clear to establish a default.

## Decision

Use independent repositories for products when they move into committed implementation. Keep the ENGINEERING LAB repository as the portfolio hub for strategy, catalogue, standards, architecture, and integration contracts.

Products must not share internal database tables by default. Cross-product communication must use explicit, documented interfaces where integration is justified.

## Consequences

### Positive
- Product boundaries and release ownership remain clear.
- Products can use different languages and infrastructure.
- The portfolio can evolve without forcing all projects into one deployment unit.

### Negative and trade-offs
- Shared improvements may need to be implemented or adapted in multiple repositories.
- Portfolio-level links and status records require maintenance.
- Cross-repository integration testing needs deliberate setup.

### Risks and mitigations
- **Risk:** duplicated implementations drift.  
  **Mitigation:** share specifications and contracts; extract common libraries only when repeated need and ownership justify them.
- **Risk:** repository sprawl.  
  **Mitigation:** create a product repository only after discovery establishes a distinct scope and committed implementation plan.

## Implementation and verification

The ENGINEERING LAB hub exists as a separate repository. Future product repositories will be created when their discovery and scope gates are met.

Verification consists of confirming product code, issue tracking, tests, and release workflows can be managed independently, and that integrations use documented contracts rather than shared database access.

## Revisit conditions

Reconsider this decision if a group of products develops substantial shared code that must be versioned and released together, or if repository coordination becomes a measurable source of risk or cost.
