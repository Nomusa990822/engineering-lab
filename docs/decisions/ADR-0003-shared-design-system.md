# ADR-0003: Define a shared design foundation while preserving product identity

- **Status:** Accepted
- **Date:** 2026-11-10
- **Decision owners:** ENGINEERING LAB
- **Related:** [DESIGN-SYSTEM.md](../../DESIGN-SYSTEM.md), [ARCHITECTURE.md](../../ARCHITECTURE.md)

## Context

The portfolio contains or may contain multiple user-facing products. A consistent baseline for accessibility, typography, spacing, interaction states, and theme behaviour can improve quality and coherence. However, forcing every product to look identical would weaken product identity and may not suit each product's users or domain.

Products may retain established visual identities rather than being redesigned merely to match the portfolio hub.

## Decision drivers

- Readability and accessibility across products.
- Consistent foundational interaction patterns.
- Support for both light and dark themes.
- Product-specific identity and usability.
- Avoidance of unnecessary shared frontend dependencies.

## Options considered

### Option A — Each product invents every design convention independently

Advantages:
- Maximum freedom for each product.
- No shared design specification to maintain.

Disadvantages:
- Repeated design decisions and inconsistent accessibility practices.
- Harder to maintain a coherent portfolio presentation.

### Option B — One rigid visual system for every product

Advantages:
- Strong visual consistency.
- Shared components may be easier to reuse.

Disadvantages:
- Can constrain products with different user needs.
- Risks forcing changes to established product identities.

### Option C — Shared foundation with product-level expression

Advantages:
- Shared accessibility and interaction principles.
- Product-specific accents and visual identity remain possible.
- Adoption can be incremental and appropriate to each product.

Disadvantages:
- Requires governance to prevent tokens and conventions drifting.
- Does not automatically create a working shared component library.

## Decision

Maintain a shared design specification with both light and dark themes; dark is the default for the portfolio direction. Products may adopt the foundation where appropriate and retain distinct product identities and accent colours.

The design document is a specification, not evidence that a shared component library or theme switch has been implemented across products.

## Consequences

### Positive
- Accessibility and interaction expectations are documented centrally.
- Products can look related without being identical.
- Adoption can occur incrementally.

### Negative and trade-offs
- Each product must validate contrast and usability in its own context.
- Design tokens and examples need periodic review.
- Shared conventions do not eliminate product-specific design work.

### Risks and mitigations
- **Risk:** visual uniformity becomes more important than usability.  
  **Mitigation:** treat product needs and accessibility as higher priority than cosmetic consistency.
- **Risk:** provisional accent colours fail contrast checks.  
  **Mitigation:** validate foreground/background combinations before implementation and adjust tokens as needed.

## Implementation and verification

DESIGN-SYSTEM.md records the shared design direction, tokens, themes, and accessibility requirements. It remains a specification. Each future implementation must be tested in both themes, including focus states, status indicators, responsive layouts, and contrast.

## Revisit conditions

Reconsider the shared foundation if user testing, accessibility review, or product requirements show that a convention is unsuitable. Update the design specification and record significant changes in a new ADR when the architectural direction changes.
