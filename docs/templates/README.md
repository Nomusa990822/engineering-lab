# Project Documentation Templates

Use these templates to make project documentation consistent without forcing every product into the same architecture or technology stack.

## Templates

| Template | Use it when |
|---|---|
| [Project README](PROJECT-README-TEMPLATE.md) | Creating or substantially restructuring a product repository's homepage |
| [Technical Specification](TECHNICAL-SPECIFICATION-TEMPLATE.md) | Defining a product, major subsystem or substantial feature before implementation |
| [Feature and Milestone Tracker](FEATURE-TRACKER-TEMPLATE.md) | Breaking work into verifiable milestones and deliverable features |
| [Development Log](DEVELOPMENT-LOG-TEMPLATE.md) | Recording a significant work session, decision, experiment or milestone |

## How to use

1. Copy the relevant template into the product repository or the appropriate project documentation folder.
2. Replace every bracketed prompt with project-specific information.
3. Delete sections that genuinely do not apply and explain important omissions.
4. Do not leave template instructions or invented example data in published project documentation.
5. Link evidence wherever possible: issues, pull requests, commits, test reports, releases and demos.
6. Keep status and claims aligned with the actual implementation.

## Naming guidance

- Use `README.md` for the product's main repository homepage.
- Use `docs/SPECIFICATION.md` or a scoped specification filename for technical specifications.
- Use `docs/PROJECT-PLAN.md` or a project-specific tracker for milestones and features.
- Use `docs/development-log/YYYY-MM-DD.md` for dated development entries.
- Use Architecture Decision Records (ADRs) for decisions with meaningful long-term consequences. See [the ADR process](../decisions/README.md).

## Portfolio-record exception for AEGIS

AEGIS portfolio documentation, progress reports, consolidated feature/milestone tracking and verification summaries are maintained in ENGINEERING LAB at [docs/projects/AEGIS.md](../projects/AEGIS.md), with dated session evidence in the portfolio development log. Do not copy these portfolio records or instantiate the generic templates inside the AEGIS Security Platform repository for this purpose. The AEGIS product repository remains independent and is used for source code and its own runtime work.

Templates are starting points, not mandatory paperwork. Prefer concise, current documentation over duplicated or stale documents.
