# Skill Improvement: Pixel New

> Purpose: Document how `pixel-new` improves the existing Pixel skill line and clarify the token-efficiency tradeoff.

## 1. Goal

`pixel-new` was created as the newest improvement of the Pixel skill:

- keep the strongest workflow ideas from the current Pixel skills
- restore the most useful missing reference material
- stay lean enough to avoid unnecessary context bloat

## 2. Source of Improvements

The previous Pixel skill line had two useful strengths:

- workflow discipline:
  - strict execution flow
  - setup-first guidance
  - QA checklist
  - explicit output contract
- reference depth:
  - token priority guidance
  - semantic token examples
  - spacing scale reference
  - stronger prop-validation reminders
  - compact component usage patterns worth preserving

## 3. What `pixel-new` Changes

| Area | Existing `pixel` | `pixel-new` |
| --- | --- | --- |
| Core workflow | Good, but split across versions | Unified and retained |
| Setup guidance | Present | Retained |
| Token guidance | Inconsistent depth | Added dedicated `design-tokens.md` |
| Component rules | Useful, but uneven | Expanded with high-value traps and mini patterns |
| Styling rules | Good | Retained with minor cleanup |
| Code structure | Good | Retained |
| Context size | Either too large or too sparse depending on version | Balanced and controlled |

## 4. New Structure

`pixel-new` uses progressive disclosure:

- `SKILL.md` contains only the operating workflow
- `references/setup.md` covers installation and token-mode checks
- `references/components.md` covers mapping, validation rules, and small patterns
- `references/design-tokens.md` covers token priority, spacing, and typography shortcuts
- `references/styling.md` covers CSS Props vs `css()`
- `references/code-structure.md` covers Vue/Nuxt output structure

This structure keeps the default load small while allowing deeper references only when needed.

## 5. Why It Is Better

`pixel-new` improves the older Pixel skill line by combining the strongest workflow guidance with the most useful reference material.

The main improvement is that it keeps execution tight while restoring the missing token guidance that agents need for real implementation work.

## 6. Token Efficiency

Measured by total line count:

| Variant | Total Lines | Notes |
| --- | --- | --- |
| Older `pixel` | 806 | Richest, but noisy and reference-heavy |
| Older `pixel3` | 244 | Most token-efficient, but missing useful token guidance |
| `pixel-new` | 346 | Best balance of execution quality and context cost |

## 7. Recommendation

- Treat the older `pixel` and `pixel3` skills as the previous Pixel baseline.
- Use **`pixel-new`** as the newest and recommended version for day-to-day Pixel implementation work.
- Keep the older skills as reference material until any remaining useful examples are either migrated or intentionally dropped.

## 8. Future Improvements

The next useful upgrades for `pixel-new` are:

- add one compact table or list pattern if real usage shows it is needed
- add composable guidance only if Pixel MCP docs confirm stable APIs
- keep examples short and validated to avoid drifting back toward the older Pixel skill size
