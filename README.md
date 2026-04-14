# Zakiy's Skills

A curated collection of [Agent Skills](https://agentskills.io/home) for frontend development and design implementation, reflecting best practices and specialized knowledge for building modern web interfaces.

## Installation

```bash
npx skills add ahmadzakiy/skills --skill 'pixel'
```

or to install all of them globally:

```bash
npx skills add ahmadzakiy/skills --skill 'pixel' -g
```

Learn more about the CLI usage at [skills](https://github.com/vercel-labs/skills).

## Skills

| Skill                                                   | Description                                                                                                                          |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| [pixel](skills/pixel)                                   | Pixel design system implementation with comprehensive reference documentation for components, design tokens, and styling conventions |
| [pixel-2026.2.18](skills/pixel-2026.2.18)               | Pinned Pixel release for reproducible use of the 2026.2.18 skill version                                                             |
| [figma-implement-design](skills/figma-implement-design) | Implementing Figma designs into code, bridging the gap between design and development, created by Figma                              |
| [frontend-design](skills/frontend-design)               | Frontend design skills with comprehensive documentation and best practices, created by Antrophic                                     |

## Versioning

Skill releases are versioned by folder name and metadata version. The repo keeps an unversioned folder such as `skills/pixel/` as the latest stable alias, and dated release folders such as `skills/pixel-2026.2.18/` for immutable snapshots.

Use the unversioned `skills/pixel/` path when you want the latest documented release, and the dated `skills/pixel-2026.2.18/` path when you need a fixed snapshot.

When a skill is updated:

1. Bump the skill metadata version in `SKILL.md`.
2. Publish or copy the new release into a versioned folder.
3. Keep the unversioned folder pointing to the latest release.
4. Regenerate `skills-lock.json` so the computed hashes match the shipped content.

The `skills-lock.json` file is a resolution lock, not the skill release version. Its top-level `version` field is the lock schema version, while each `computedHash` tracks the exact content of a skill at publish time.

## License

MIT
