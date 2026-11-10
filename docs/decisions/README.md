# Architecture Decision Records

Architecture Decision Records (ADRs) capture significant technical and product-architecture decisions, including the context, alternatives, consequences, and conditions for revisiting them.

## When to write an ADR

Create an ADR when a decision materially affects one or more of:
- system boundaries or service ownership;
- data storage, consistency, or migration;
- public APIs, event contracts, or integrations;
- security, identity, privacy, or trust boundaries;
- technology choices that are expensive to reverse;
- deployment, reliability, or operational design.

Routine implementation details do not need an ADR.

## Status values

- **Proposed:** under discussion; not yet adopted.
- **Accepted:** chosen direction; implementation may still be pending.
- **Superseded:** replaced by a later ADR.
- **Deprecated:** no longer recommended, but not necessarily replaced.

An Accepted ADR records a decision, not proof that the decision has been implemented.

## Naming and structure

Use sequential identifiers and descriptive filenames:

`ADR-0001-independent-product-repositories.md`

Each ADR should contain:
1. Title and status.
2. Date.
3. Context and problem.
4. Decision drivers.
5. Considered options.
6. Decision.
7. Consequences and trade-offs.
8. Implementation and verification notes.
9. Related decisions.

Do not edit history to hide a changed decision. Create a new ADR that supersedes the earlier one and link the records.

## Creating a new ADR

1. Copy [ADR-TEMPLATE.md](ADR-TEMPLATE.md).
2. Assign the next unused number.
3. Replace all prompts with concrete information.
4. Link relevant architecture, roadmap, or integration documents.
5. Update the status only when the decision is actually made.

ADRs describe ENGINEERING LAB decisions. Individual products may maintain their own ADRs for product-specific decisions.
