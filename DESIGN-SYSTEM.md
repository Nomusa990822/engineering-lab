# Engineering Lab Design System

**Version:** 1.0  
**Status:** Foundation specification  
**Scope:** Portfolio hub and future independent products

> SOFTWARE · SYSTEMS · INTELLIGENCE · RESEARCH

## 1. Purpose

The Engineering Lab design system defines a consistent, accessible visual language for the portfolio hub and its independent software products. It provides shared foundations without forcing every product to look identical.

The system is framework-agnostic. Products may use different frontend frameworks or rendering approaches, but should map their interfaces to the semantic tokens and interaction principles defined here.

## 2. Design principles

1. **Clarity before decoration.** Layout, labels and information hierarchy must make complex systems understandable.
2. **Consistency without uniformity.** Shared foundations create coherence; each product retains a distinct identity.
3. **Functional density.** Technical dashboards may present substantial information, but must remain readable and navigable.
4. **Accessible by default.** Keyboard operation, visible focus, semantic structure, contrast and reduced-motion preferences are requirements.
5. **Responsive by design.** Interfaces must work on narrow mobile screens, tablets and desktop displays.
6. **Honest status communication.** Loading, empty, success, warning and error states must be explicit. Colour must never be the only indicator.
7. **Measured polish.** Motion, shadows, gradients and decorative effects should support hierarchy rather than compete with content.

## 3. Theme model

Engineering Lab supports both dark and light themes.

- **Default:** dark.
- **User control:** a clearly labelled theme control in the primary navigation.
- **Persistence:** save an explicit user selection in browser storage using the key `engineering-lab-theme`.
- **First visit:** use dark mode unless a future product-specific requirement explicitly changes this decision.
- **Scope:** theme selection applies consistently across the hub and products that adopt the shared system.
- **Completeness:** theme changes must affect backgrounds, surfaces, text, borders, overlays, charts, focus indicators and component states—not only the page background.

Use the root attribute `data-theme="dark"` or `data-theme="light"`. Components must consume semantic tokens rather than hard-coded theme-specific colours.

## 4. Colour tokens

### 4.1 Dark theme

| Token | Value | Intended use |
|---|---|---|
| `--color-background` | `#0B0F14` | Application background |
| `--color-surface` | `#1C2836` | Cards, panels and navigation |
| `--color-surface-elevated` | `#263548` | Menus, dialogs and elevated panels |
| `--color-text` | `#E8EEF5` | Primary text |
| `--color-text-muted` | `#94A3B8` | Secondary text |
| `--color-border` | `#334155` | Dividers and component boundaries |
| `--color-accent` | `#2F80FF` | Primary actions and links |
| `--color-accent-strong` | `#60A5FA` | Hover and emphasis |
| `--color-focus` | `#93C5FD` | Keyboard focus indicator |

### 4.2 Light theme

| Token | Value | Intended use |
|---|---|---|
| `--color-background` | `#F8FAFC` | Application background |
| `--color-surface` | `#FFFFFF` | Cards, panels and navigation |
| `--color-surface-elevated` | `#F1F5F9` | Menus, dialogs and elevated panels |
| `--color-text` | `#0F172A` | Primary text |
| `--color-text-muted` | `#475569` | Secondary text |
| `--color-border` | `#E2E8F0` | Dividers and component boundaries |
| `--color-accent` | `#2563EB` | Primary actions and links |
| `--color-accent-strong` | `#1D4ED8` | Hover and emphasis |
| `--color-focus` | `#1D4ED8` | Keyboard focus indicator |

### 4.3 Semantic status tokens

Status colours are semantic and must be accompanied by text, an icon with an accessible label, or another non-colour cue.

| Meaning | Dark theme | Light theme |
|---|---|---|
| Success | `#4ADE80` | `#15803D` |
| Warning | `#FBBF24` | `#A16207` |
| Danger | `#F87171` | `#B91C1C` |
| Information | `#60A5FA` | `#1D4ED8` |

These values are initial design tokens, not a claim of completed accessibility certification. Validate foreground/background combinations and focus visibility during implementation. Adjust component-level pairings where necessary.

## 5. CSS foundation

The following is the canonical starting point for shared theme tokens:

```css
:root {
  color-scheme: dark;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", sans-serif;

  --font-size-xs: 0.75rem;
  --font-size-sm: 0.875rem;
  --font-size-md: 1rem;
  --font-size-lg: 1.125rem;
  --font-size-xl: 1.25rem;
  --font-size-2xl: 1.5rem;
  --font-size-3xl: 1.875rem;

  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-5: 1.25rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-10: 2.5rem;
  --space-12: 3rem;
  --space-16: 4rem;

  --radius-sm: 0.375rem;
  --radius-md: 0.625rem;
  --radius-lg: 0.875rem;
  --radius-xl: 1.125rem;
  --radius-pill: 999px;

  --shadow-sm: 0 1px 2px rgb(0 0 0 / 0.18);
  --shadow-md: 0 8px 24px rgb(0 0 0 / 0.22);
  --shadow-lg: 0 18px 48px rgb(0 0 0 / 0.28);
}

:root,
:root[data-theme="dark"] {
  color-scheme: dark;
  --color-background: #0B0F14;
  --color-surface: #1C2836;
  --color-surface-elevated: #263548;
  --color-text: #E8EEF5;
  --color-text-muted: #94A3B8;
  --color-border: #334155;
  --color-accent: #2F80FF;
  --color-accent-strong: #60A5FA;
  --color-focus: #93C5FD;
  --color-success: #4ADE80;
  --color-warning: #FBBF24;
  --color-danger: #F87171;
  --color-info: #60A5FA;
}

:root[data-theme="light"] {
  color-scheme: light;
  --color-background: #F8FAFC;
  --color-surface: #FFFFFF;
  --color-surface-elevated: #F1F5F9;
  --color-text: #0F172A;
  --color-text-muted: #475569;
  --color-border: #E2E8F0;
  --color-accent: #2563EB;
  --color-accent-strong: #1D4ED8;
  --color-focus: #1D4ED8;
  --color-success: #15803D;
  --color-warning: #A16207;
  --color-danger: #B91C1C;
  --color-info: #1D4ED8;
}

body {
  margin: 0;
  background: var(--color-background);
  color: var(--color-text);
}

:focus-visible {
  outline: 2px solid var(--color-focus);
  outline-offset: 3px;
}

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

## 6. Theme switching behaviour

Implement theme switching as a small, framework-independent service or equivalent framework feature.

Required behaviour:

1. Read `engineering-lab-theme` when the application starts.
2. If the stored value is exactly `light`, apply light; otherwise apply dark.
3. Set the root `data-theme` attribute.
4. When the user switches theme, update the attribute and persist the new value.
5. Expose the current theme and action with an accessible name, such as “Switch to light theme” or “Switch to dark theme”.
6. Do not make theme switching dependent on an icon alone.
7. Avoid a flash of the wrong theme by applying the saved value before the main interface is painted where the application architecture permits.

Do not store sensitive information in local storage. The theme preference is non-sensitive.

## 7. Typography

- Primary typeface: Inter, with system sans-serif fallbacks.
- Use a clear hierarchy rather than many font weights.
- Body text should generally be 1rem with comfortable line height.
- Use tabular numerals for metrics, timestamps and aligned numeric tables where appropriate.
- Use monospace typography for code, identifiers, logs and terminal output.
- Avoid long lines in documentation and dense interface panels.

## 8. Layout and spacing

- Use a consistent spacing scale based on 4px increments.
- Align content to a deliberate grid.
- Use a readable maximum width for long-form documentation.
- Allow data-heavy dashboards to use wider layouts when justified.
- Preserve adequate whitespace around headings, controls and important data.
- On narrow screens, collapse navigation and reflow multi-column layouts without horizontal page overflow.

## 9. Components and interaction states

Shared components should define consistent states:

- **Buttons:** primary, secondary, quiet and destructive variants; default, hover, focus-visible, active, disabled and loading states.
- **Inputs:** visible labels, help text, validation messages, focus and disabled states.
- **Cards and panels:** consistent surface, border, radius and spacing tokens.
- **Tables:** semantic headers, readable density, responsive overflow strategy and clear empty states.
- **Dialogs and menus:** keyboard access, focus management, escape behaviour and clear dismissal.
- **Alerts and badges:** explicit status text and semantic meaning.
- **Charts:** labelled axes, readable legends, accessible summaries and theme-aware grid/label colours.

Do not rely on placeholder text as the only input label. Do not communicate errors or success through colour alone.

## 10. Product identity and accent colours

Products may use a distinct accent while retaining shared semantic theme tokens and component behaviour. Initial accent proposals:

| Product | Accent |
|---|---|
| SENTINEL QA | `#D97706` |
| MERIDIAN | `#2563EB` |
| ORBIT | `#7C3AED` |
| FORGE | `#C2410C` |
| NEXUS | `#4338CA` |
| GITFORGE | `#64748B` |
| ATLAS | `#B91C1C` |
| CHRONOS | `#6D28D9` |
| NEBULA | `#0369A1` |
| OBSERVA | `#A16207` |
| CORTEX | `#8B5CF6` |
| ORACLE | `#9A3412` |
| SYNAPSE | `#A21CAF` |
| VELOCITY | `#DC2626` |
| HELIOS | `#B45309` |
| AURORA | `#1D4ED8` |
| POLARIS | `#075985` |
| QUANTUM | `#5B21B6` |
| PHOENIX | `#9F1239` |

These are provisional identity choices. Before use, verify contrast against both themes and adjust derived foregrounds or tints as needed. A product accent must not replace success, warning, danger or information colours.

## 11. Accessibility and quality gates

Before a shared component is considered ready:

- Check text contrast against WCAG 2.2 AA requirements where applicable.
- Confirm visible keyboard focus and logical focus order.
- Confirm all controls have accessible names and labels.
- Confirm the interface remains usable at 200% zoom.
- Confirm content reflows at narrow viewport widths.
- Confirm status is not conveyed by colour alone.
- Respect reduced-motion preferences.
- Test both light and dark themes, including charts, dialogs, menus and validation states.

## 12. Governance

- Shared token changes must be documented and reviewed.
- Product-specific exceptions must be intentional and documented.
- Avoid hard-coded colours where semantic tokens exist.
- Do not introduce a new design token for a one-off cosmetic preference without a reusable need.
- Update this document when a shared rule changes.

## 13. Implementation status

This document is the design-system specification. It does not claim that a working component library, theme switch, accessibility audit or visual regression suite has already been implemented. Those will be built and verified as part of the portfolio hub and product work.
