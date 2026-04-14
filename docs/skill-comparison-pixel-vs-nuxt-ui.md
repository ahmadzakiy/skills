# Skill Comparison: Nuxt UI vs Pixel

> **Purpose:** Compare the `nuxt-ui` and `pixel` agent skills, and identify the best practices from `nuxt-ui` that can be adopted to improve the `pixel` skill.

---

## 1. Overview

| Aspect | Nuxt UI Skill | Pixel Skill |
|---|---|---|
| **Design System** | `@nuxt/ui` v4 — 125+ components | `@mekari/pixel3` — Mekari's proprietary design system |
| **Styling Engine** | Tailwind CSS + Tailwind Variants | CSS Props + `css()` function + Design Tokens |
| **Target Stack** | Nuxt, Vue (Vite), Laravel (Inertia), AdonisJS | Nuxt 4, Vue 3 |
| **Component Count** | 125+ components | Curated Mekari components (MpButton, MpFlex, etc.) |
| **Icon System** | Iconify — 200,000+ icons | Pixel's own icon set via `MpIcon` |
| **Form Validation** | Standard Schema (Zod, Valibot, Yup, Joi) | Manual ref-based validation |
| **Theming** | Runtime color config + CSS variables | Design Token 2.1 / 2.4 semantic tokens |
| **Dark Mode** | Built-in via `useColorMode()` | Not explicitly documented |
| **Layout Templates** | 5 named layouts + 13 starter templates | No pre-built layouts |
| **Composables** | `useToast`, `useOverlay`, `defineShortcuts` | Not documented in skill |
| **MCP Tools** | External: Nuxt UI MCP docs | `get-docs`, `get-component` (Pixel MCP) |
| **Figma Integration** | Not mentioned | Deeply integrated (Figma MCP tools) |

---

## 2. Structural Comparison

### 2.1 Installation & Setup

**Nuxt UI** includes explicit multi-framework installation instructions (Nuxt, Vue/Vite, Laravel, AdonisJS) with complete code examples for each path, including the required `<UApp>` root wrapper and its purpose.

**Pixel** references setup via the MCP tool (`get-docs`) rather than embedding it in the skill itself. Agents must first query the MCP to discover installation steps.

### 2.2 Theming & Design Tokens

**Nuxt UI** has a comprehensive *Brand Customization Playbook* — a structured 5-step process covering color palettes, fonts, CSS variables, global component overrides, and dark mode verification. Semantic utilities (`text-default`, `bg-elevated`, `border-muted`) are exhaustively documented in a table with light/dark mode values.

**Pixel** uses a Design Token priority hierarchy (2.4 → 2.1 → raw hex) and semantic tokens like `text.primary`, `background.surface`. However, theming customization and dark mode support are not addressed in the skill.

### 2.3 Component Documentation

**Nuxt UI** provides a flat categorized table (Layout, Element, Form, Data, Navigation, Overlay) with key props for all 125+ components in a single reference file. Components with complex usage include full code examples.

**Pixel** includes a Figma-to-component mapping table, a prop validation section (with explicit ❌ / ✅ anti-pattern examples), and common usage patterns (forms, cards, modals). Enforcement of correct prop values is a unique strength here.

### 2.4 Form Handling

**Nuxt UI** integrates with Standard Schema for declarative, schema-driven validation across multiple libraries.

**Pixel** uses a manual `ref`-based pattern with `MpFormControl` / `MpFormErrorMessage` wrappers. No schema-based validation approach is documented.

### 2.5 Overlays & Composables

**Nuxt UI** documents programmatic overlay creation via `useOverlay()`, toast notifications via `useToast()`, and keyboard shortcuts via `defineShortcuts()`.

**Pixel** documents overlay components (MpModal, MpDrawer) declaratively but does not document composable or programmatic access patterns.

### 2.6 Layout System

**Nuxt UI** ships with 5 pre-composed layout patterns (Page, Dashboard, Docs, Chat, Editor) with dedicated reference files, plus 13 official starter templates on GitHub.

**Pixel** has no layout system or templates documented in the skill.

### 2.7 Figma Integration

**Pixel** deeply integrates with Figma via MCP tools (`get_design_context`, `get_screenshot`, `get_metadata`) — this is a significant advantage the Nuxt UI skill does not have.

---

## 3. Best Parts of Nuxt UI to Implement in Pixel Skill

The following improvements are ranked by **impact** — how much they would improve the agent's ability to produce correct, consistent output.

### 3.1 Brand Customization Playbook ⭐ High Impact

**What Nuxt UI does:**
A step-by-step guide (Define colors → Set fonts → Adjust CSS variables → Override components globally → Verify dark mode) with a quick checklist table.

**Why it matters for Pixel:**
Agents working with Pixel frequently need to match a brand or adapt the theme. Without a structured playbook, agents make ad-hoc decisions. Adding a similar guide using Pixel's Design Token system would prevent inconsistencies.

**How to implement:**
Add a `## Theme Customization Playbook` section to `references/styling.md` or `references/design-tokens.md` covering:
1. Choose between Design Token 2.1 and 2.4
2. Map brand colors to Pixel semantic tokens
3. Override component defaults via the Pixel theming API
4. Verify output across contexts

---

### 3.2 Schema-Based Form Validation ⭐ High Impact

**What Nuxt UI does:**
Documents `UForm` + `UFormField` with Standard Schema (Zod, Valibot), with a full working example showing schema definition, reactive state, and `@submit` emission.

**Why it matters for Pixel:**
The Pixel skill only shows manual `isError` ref patterns. Production applications almost always require declarative form validation. Agents should know how to integrate Zod or Valibot with `MpFormControl`.

**How to implement:**
Add a `### Form with Schema Validation` section to `references/components.md` showing a complete example with Zod + `MpFormControl` + `MpFormErrorMessage`.

---

### 3.3 Semantic Utility Color Tables ⭐ High Impact

**What Nuxt UI does:**
Provides complete tables mapping each semantic utility (`text-default`, `bg-elevated`, `border-muted`) to its actual light and dark mode values. Agents always know what token to reach for in any context.

**Why it matters for Pixel:**
Pixel's `references/design-tokens.md` documents tokens individually but doesn't provide a structured table with use-case descriptions and light/dark mode values side by side.

**How to implement:**
Restructure `references/design-tokens.md` to add tables like:

| Token | Use Case | Design Token 2.4 | Design Token 2.1 |
|---|---|---|---|
| `text.primary` | Primary content text | `text.primary` | `gray.900` |
| `background.surface` | Card/panel background | `background.surface` | `white` |
| `border.default` | Default borders | `border.default` | `gray.200` |

---

### 3.4 Composable Patterns (Toasts & Programmatic Overlays) ⭐ Medium Impact

**What Nuxt UI does:**
Documents `useToast()`, `useOverlay()`, and `defineShortcuts()` with concise usage examples. Agents can immediately produce notification and programmatic modal code.

**Why it matters for Pixel:**
If Pixel has equivalent composables (e.g., for toasts or programmatic modals), agents don't know about them. If it doesn't, noting this gap is itself useful guidance.

**How to implement:**
Add a new `references/composables.md` to the Pixel skill (or a `## Composables` section in `SKILL.md`) documenting any available hooks — or explicitly noting that overlays must be used declaratively.

---

### 3.5 Pre-Composed Layout Patterns ⭐ Medium Impact

**What Nuxt UI does:**
Provides 5 dedicated layout reference files (Dashboard, Docs, Chat, Editor, Page) so agents can load only the relevant pattern, reducing context usage.

**Why it matters for Pixel:**
Agents building dashboards or admin UIs with Pixel have no reference for how to structure `MpFlex`-based layouts at the page level. Common recurring layouts (sidebar + main, header + content, two-panel) are not documented.

**How to implement:**
Add a `references/layouts/` directory to the Pixel skill with layout references such as:
- `dashboard.md` — sidebar navigation + main content area
- `page.md` — centered content with header/footer
- `form-page.md` — form-centric layouts

---

### 3.6 Multi-Framework Setup Instructions ⭐ Low Impact (Pixel-specific)

**What Nuxt UI does:**
Documents setup for 4 different frameworks with full, copy-paste-ready code blocks.

**Why it matters for Pixel:**
Pixel targets Nuxt 4 and Vue 3. Within those two stacks the setup differs and agents currently rely entirely on MCP tool calls to discover this. Embedding the core setup inline in `SKILL.md` would reduce MCP round-trips for new projects.

**How to implement:**
Add an `## Installation` section to `SKILL.md` with minimal but complete setup code for both Nuxt 4 and Vue 3 + Vite, similar to the nuxt-ui skill's installation block.

---

### 3.7 Global Component Theme Override Pattern ⭐ Low Impact

**What Nuxt UI does:**
Explains override priority (`ui` prop > global config > theme defaults), slot-based customization, and compound variants — with explicit examples for both global (`app.config.ts`) and per-instance patterns.

**Why it matters for Pixel:**
Agents currently have no guidance on how to override Pixel component defaults globally. Adding a section explaining Pixel's theming extension API would reduce per-instance workarounds.

**How to implement:**
Add a `### Global Component Overrides` section to `references/styling.md` documenting how Pixel's theme system works and where to configure global defaults.

---

## 4. What Pixel Does Better (Strengths to Preserve)

| Strength | Description |
|---|---|
| **Figma Integration** | Deep, structured Figma-to-component workflow with MCP tools — not present in nuxt-ui skill |
| **Prop Validation Anti-Patterns** | Explicit ❌ / ✅ examples prevent invalid prop usage (e.g., `MpText size="md"`) — nuxt-ui skill doesn't have this |
| **MCP-Driven Documentation** | Using `get-component` for live, up-to-date docs avoids stale inlined references |
| **Token Priority Hierarchy** | Clear 3-level fallback (2.4 → 2.1 → hex) gives agents a decision framework nuxt-ui lacks |
| **CSS Prop Constraint Rules** | Explicit rules about when to use CSS Props vs `css()` function prevent common styling mistakes |
| **Strict SFC Block Order** | The `<template>` first rule with ❌ / ✅ examples is a clear, enforceable code quality rule |

---

## 5. Summary: Implementation Roadmap

| Priority | Improvement | Target File |
|---|---|---|
| 🔴 High | Schema-based form validation example | `references/components.md` |
| 🔴 High | Semantic token table with use cases + light/dark values | `references/design-tokens.md` |
| 🔴 High | Theme customization playbook | `references/styling.md` |
| 🟡 Medium | Composables reference (toasts, programmatic overlays) | `references/composables.md` (new) |
| 🟡 Medium | Layout patterns reference | `references/layouts/` (new directory) |
| 🟢 Low | Inline installation section for Nuxt 4 + Vue 3 | `SKILL.md` |
| 🟢 Low | Global component override pattern | `references/styling.md` |
