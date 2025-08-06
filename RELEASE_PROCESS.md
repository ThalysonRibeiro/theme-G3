# Release Process

This document outlines the steps to publish a new version of the G3 Theme Pack. The process is automated using GitHub Actions.

## Prerequisites

- Ensure you have committed all your code changes to the `develop` branch.
- Ensure the `VSCE_PAT` secret is correctly configured in the repository's Actions secrets.

## Step-by-Step Guide

### 1. Update Version Number

Open `package.json` and increment the `version` field. For example, change `"version": "0.0.4"` to `"version": "0.0.5"`.

### 2. Update Changelog

Open `CHANGELOG.md` and add a new entry for the version you are about to release. Follow the existing format.

```markdown
## [0.0.5] - YYYY-MM-DD

### Added

- New feature description.

### Changed

- Description of a change.

### Fixed

- Description of a bug fix.
```

### 3. Commit the Changes

Stage and commit the updated `package.json` and `CHANGELOG.md` files.

```bash
git add package.json CHANGELOG.md
git commit -m "chore: Prepare release v0.0.5"
```

### 4. Push the Commit

Push the commit to your main branch on GitHub.

```bash
git push origin develop
```

### 5. Create and Push the Git Tag

This is the step that triggers the automated release pipeline. Create a new Git tag that matches the version in `package.json` and push it to the repository.

```bash
# Create the tag
git tag v0.0.5

# Push the tag to GitHub
git push origin v0.0.5
```

### 6. Verify the Release

Once you push the tag, the GitHub Actions pipeline will start automatically.

- You can monitor its progress in the **Actions** tab of the repository.
- If it succeeds:
  - A new release will be created in the **Releases** section of the repository, with the `.vsix` file attached.
  - The new version will be published to the VS Code Marketplace.
