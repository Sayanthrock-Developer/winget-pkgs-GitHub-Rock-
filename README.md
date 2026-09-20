# GitHub Rock — WinGet Packages

[![GitHub Rock](https://img.shields.io/badge/GitHub-Rock-181717?logo=github)](https://github.com/Sayanthrock-Developer/GitHub-Rock)
[![WinGet](https://img.shields.io/badge/WinGet-manifests-0078D4)](https://learn.microsoft.com/windows/package-manager/)
[![Manifest validation](https://github.com/Sayanthrock-Developer/winget-pkgs-GitHub-Rock-/actions/workflows/validate-manifests.yml/badge.svg)](https://github.com/Sayanthrock-Developer/winget-pkgs-GitHub-Rock-/actions/workflows/validate-manifests.yml)

Community WinGet package manifests for **GitHub Rock**.

This repository is the Windows distribution layer for GitHub Rock. Application source code and release engineering remain in the [main GitHub Rock repository](https://github.com/Sayanthrock-Developer/GitHub-Rock).

## What belongs here

- Official WinGet manifest files for released GitHub Rock Windows versions.
- Manifest documentation and contribution tooling.
- Validation workflows that keep package metadata consistent.

**No placeholder package, installer, version, URL, or SHA256 value is accepted.** A manifest is added only after a real GitHub Rock Windows installer has been published.

## Repository layout

    .github/
    ├── CODEOWNERS
    ├── PULL_REQUEST_TEMPLATE.md
    └── workflows/
        └── validate-manifests.yml
    docs/README.md
    manifests/<publisher>/<package>/<version>/
    README.md

## Manifest rules

- Follow the official [WinGet manifest schema](https://github.com/microsoft/winget-pkgs/tree/master/doc/manifest/schema).
- Use the exact package identifier and released version.
- Keep one package/version update per pull request.
- Installer URLs must be stable, public, and point to the exact released installer.
- SHA256 must be calculated from that exact installer.
- Do not commit installers, binaries, generated archives, or application source.
- Never reuse a hash from another release.
- Never create a manifest for an unreleased or unavailable installer.

## Validate locally

From Windows with WinGet installed:

    winget validate --manifest <path-to-version-folder>

Then test the exact manifest:

    winget install --manifest <path-to-version-folder>

For an installer hash:

    (Get-FileHash .\GitHub-Rock-<version>.exe -Algorithm SHA256).Hash

CI validates manifests on pull requests and pushes that change manifests or validation tooling.

## Release flow

GitHub Rock Windows release → public installer → SHA256 → WinGet manifest → local validation → pull request → CI validation → merge

## Related projects

- **GitHub Rock:** https://github.com/Sayanthrock-Developer/GitHub-Rock
- **GitHub Rock Backend:** https://github.com/Sayanthrock-Developer/GitHub-Rock-Backend
- **WinGet documentation:** https://learn.microsoft.com/windows/package-manager/
- **WinGet community repository:** https://github.com/microsoft/winget-pkgs

## Contributing

Read [docs/README.md](docs/README.md) before adding or updating a manifest. Keep changes focused, traceable to a real GitHub Rock release, and verifiable by WinGet.