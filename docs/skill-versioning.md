# Skill Versioning

This repository uses two layers of versioning:

1. Skill release versions, stored in the skill metadata and folder name.
2. Lockfile versions, stored in `skills-lock.json`.

## Release Versioning

Use a versioned folder for each immutable skill release, for example:

- `skills/pixel-2026.2.18/`

Inside that folder, keep the skill metadata version aligned with the folder version:

- `metadata.version: "2026.2.18"`

Keep an unversioned folder for the latest stable release when you want a stable import path:

- `skills/pixel/`

That gives you both:

- a stable alias for consumers who always want latest
- a pinned snapshot for consumers who need reproducible behavior

## Lockfile Versioning

`skills-lock.json` is not the skill release version. It records the resolved content hash for each installed skill plus a lock schema version.

- `version` at the top of the file is the lock schema version.
- `computedHash` entries change whenever a skill file changes.

Regenerate the lock file after any skill update so the hashes match the published content.

## Update Flow

1. Make the skill change.
2. Update the release version in the skill metadata.
3. Copy or publish the release into a versioned folder.
4. Keep the unversioned folder on the latest release if needed.
5. Refresh `skills-lock.json`.

## Recommended Convention

For this repo, use calendar versions in the form `YYYY.M.DD` for skill releases, because that already matches the existing Pixel release naming.
