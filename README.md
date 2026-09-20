# GitHub Rock — WinGet Packages

[![GitHub](https://img.shields.io/badge/GitHub-Rock-181717?logo=github)](https://github.com/Sayanthrock-Developer/GitHub-Rock)
[![WinGet](https://img.shields.io/badge/WinGet-package%20manifests-0078D4)](https://learn.microsoft.com/windows/package-manager/)

Community WinGet manifests for **GitHub Rock**.

This repository is intentionally focused on package metadata and contribution tooling. Application source code belongs in the main [GitHub Rock repository](https://github.com/Sayanthrock-Developer/GitHub-Rock).

## Repository layout

```text
.
├── .github/
│   ├── CODEOWNERS
│   ├── copilot-instructions.md
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
├── docs/
│   └── README.md
├── manifests/
│   └── <publisher>/<package>/<version>/
├── .editorconfig
└── .gitattributes
```

## Manifest policy

- Keep one package/version update per pull request.
- Use the official WinGet manifest schema.
- Do not commit generated binaries or installers.
- Installer URLs must point to a stable, publicly accessible release.
- SHA256 values must match the referenced installer.
- Validate manifests before submitting a pull request.
- Do not add a manifest until a corresponding GitHub Rock Windows installer is published.

## Local validation

From a Windows machine with WinGet installed:

```powershell
winget validate --manifest <path-to-version-folder>
```

For an installation test:

```powershell
winget install --manifest <path-to-version-folder>
```

## Source

- GitHub Rock: https://github.com/Sayanthrock-Developer/GitHub-Rock
- WinGet documentation: https://learn.microsoft.com/windows/package-manager/
- WinGet manifest specification: https://github.com/microsoft/winget-pkgs/tree/master/doc/manifest/schema

## Contributing

Open a pull request with a focused manifest change. The pull-request template and CI checks are designed to catch formatting and manifest-validation problems before merge.
