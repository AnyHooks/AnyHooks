# Semantic Versioning (SemVer) in AnyHooks Project Workflow

## Introduction

This document outlines how to implement Semantic Versioning (SemVer) in the AnyHooks project workflow. The versioning follows the SemVer 2.0.0 specification, which you can read in detail [here](https://semver.org).

## Version Format

The version format follows the `x.y.z` pattern, where:

- `x` is the Major version
- `y` is the Minor version
- `z` is the Patch version

### Pre-release Labels

Pre-release versions may include an additional label appended to the version. Examples include `-alpha`, `-beta`, `-rc.1` etc.

## Workflow Steps

### 1. Initial Development

For initial development, you can use `0.y.z` where `y` and `z` can be incremented as needed.

```bash
git tag -a v0.1.0-alpha -m "Initial development"
git push origin v0.1.0-alpha
```

### 2. Feature Addition or Minor Changes

For adding new features or making minor changes, increment the Minor version (`y`).

```bash
git tag -a v0.2.0-alpha -m "New feature added"
git push origin v0.2.0-alpha
```

### 3. Patch or Bug Fixes

For patches or bug fixes, increment the Patch version (`z`).

```bash
git tag -a v0.2.1-alpha -m "Bug fix"
git push origin v0.2.1-alpha
```

### 4. Major Changes

For breaking changes or major overhauls, increment the Major version (`x`).

```bash
git tag -a v1.0.0 -m "Major changes"
git push origin v1.0.0
```

### 5. Pre-release to Final Release

To move from a pre-release version to a final release, remove the pre-release label.

```bash
git tag -a v1.0.0 -m "Final release"
git push origin v1.0.0
```

## Conclusion

By following this versioning scheme, the AnyHooks project can maintain a clear and organized version history, making it easier for users and contributors to understand the state and stability of the project.