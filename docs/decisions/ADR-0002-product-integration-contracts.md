# ADR-0002: Integrate products through explicit contracts

- **Status:** Accepted
- **Date:** 2026-11-10
- **Decision owners:** ENGINEERING LAB
- **Related:** [ARCHITECTURE.md](../../ARCHITECTURE.md), [INTEGRATION-STRATEGY.md](../../INTEGRATION-STRATEGY.md), [ADR-0001](ADR-0001-independent-product-repositories.md)

## Context

Independent products may eventually exchange information or coordinate work. Direct access to another product's internal database or implementation would create hidden dependencies and make independent changes risky.

The portfolio needs a consistent default for deciding how products communicate while preserving the ability to choose a simpler mechanism when appropriate.

## Decision drivers

- Explicit ownership of data and behaviour.
- Security and least-privilege access.
- Versionable and testable interfaces.
- Failure isolation and operational visibility.
- Avoidance of unnecessary infrastructure.

## Options considered

### Option A — Direct database sharing

Advantages:
- Can be quick for a small prototype.
- Avoids implementing an API for simple reads.

Disadvantages:
- Couples products to internal schemas and migrations.
- Makes access control and ownership unclear.
- Allows one product's failure or change to affect another unexpectedly.

### Option B — Explicit APIs, events, webhooks, or controlled exchanges

Advantages:
- Contracts can be documented, versioned, tested, and secured.
- Each product retains ownership of its data.
- Integration mechanisms can match the communication need.

Disadvantages:
- Requires contract design and integration testing.
- Adds network, delivery, and operational failure modes.

### Option C — No integration

Advantages:
- Maximum independence and minimum integration complexity.

Disadvantages:
- Prevents useful cross-product workflows where they have genuine value.

## Decision

When integration is justified, use an explicit contract. Choose synchronous APIs for request/response interactions, events for asynchronous facts and notifications, webhooks for controlled outbound notifications, and batch or human-mediated exchange where that is simpler and safer.

Do not share internal database tables as an integration mechanism. Do not introduce a message broker, gateway, or distributed infrastructure unless the requirements justify it.

## Consequences

### Positive
- Data ownership remains with the producing product.
- Interfaces can be tested independently and in integration.
- Authentication, authorisation, validation, and versioning can be designed at the boundary.

### Negative and trade-offs
- Contracts and compatibility need maintenance.
- Network calls and asynchronous delivery introduce failure cases.
- End-to-end workflows need explicit observability and troubleshooting.

### Risks and mitigations
- **Risk:** incompatible contract changes.  
  **Mitigation:** version interfaces where necessary, define compatibility expectations, and test consumers before rollout.
- **Risk:** duplicate or delayed event delivery.  
  **Mitigation:** define delivery semantics, idempotency, retry limits, and replay behaviour for each event integration.
- **Risk:** excessive infrastructure.  
  **Mitigation:** start with the simplest mechanism that satisfies the use case.

## Implementation and verification

The portfolio integration strategy documents the contract principles. Specific integrations remain unimplemented until their contracts, security controls, tests, and operational behaviour are delivered and verified.

## Revisit conditions

Reconsider this decision if a concrete integration demonstrates that another pattern is materially simpler, safer, or more reliable. Record the exception and its consequences in a new ADR rather than silently bypassing the standard.
