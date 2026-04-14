# Skill Comparison: Pixel vs Pixel3

> Purpose: Explain what changed in `pixel3` compared with `pixel`, and when to use each.

## 1. High-Level Difference

| Aspect              | `pixel` skill                                                 | `pixel3` skill                                                                |
| ------------------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Core focus          | Pixel implementation guide with broad references and MCP list | Workflow-first implementation playbook optimized for execution reliability    |
| Trigger description | Good but includes extra metadata in frontmatter               | Cleaner frontmatter (`name` + `description`) aligned with skill-creator rules |
| Structure           | Long single skill doc + references                            | Lean skill doc + focused references with explicit checkpoints                 |
| Setup guidance      | Mostly "use MCP to check setup"                               | Adds concrete pre-implementation checklist and token-mode checks              |
| Implementation flow | Step-based, but less constrained on verification              | Deterministic flow: setup -> analyze -> map -> implement -> style -> QA       |
| Output expectations | Output format section                                         | Explicit output contract + QA checklist for delivery consistency              |
| UI metadata         | No `agents/openai.yaml` in this repo copy                     | Includes `agents/openai.yaml` for UI chip metadata and default prompt         |

## 2. Content-Level Changes

### What `pixel3` adds

1. A stricter execution workflow that reduces ambiguity during implementation.
2. A dedicated `setup.md` reference with readiness checks before coding.
3. A clearer separation of concerns across references:
   - `components.md` for mapping and prop-validation rules
   - `styling.md` for token-safe styling hierarchy
   - `code-structure.md` for SFC and TypeScript structure
4. A final QA checklist (states, responsiveness, token safety).
5. A standardized delivery contract for output completeness.

### What `pixel` still has (and `pixel3` intentionally simplifies)

1. More narrative context and broader MCP references in one place.
2. Extra metadata fields in frontmatter (`metadata.author`, `version`, `source`).
3. More detailed examples directly embedded in references.

## 3. Design Philosophy Difference

| Dimension              | `pixel`                | `pixel3`                                 |
| ---------------------- | ---------------------- | ---------------------------------------- |
| Guidance style         | Reference-heavy        | Execution-heavy                          |
| Skill body size        | Larger and descriptive | Smaller and directive                    |
| Token efficiency       | Moderate               | Higher (progressive disclosure emphasis) |
| Consistency guardrails | Present                | Stronger and more explicit               |

## 4. When to Use Which

- Use **`pixel3`** for day-to-day implementation tasks where you want a predictable, production-oriented workflow and cleaner context usage.
- Use **`pixel`** as a deeper reference source when you need broader narrative guidance or additional examples.

## 5. Suggested Next Improvement

To fully supersede `pixel`, migrate the most valuable long-form examples from `pixel/references/*.md` into `pixel3/references/` only where they improve correctness (especially complex form, modal, and table patterns).
