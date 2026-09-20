# GitHub Rock WinGet repository instructions

This repository contains WinGet package manifests for GitHub Rock. It is not the application source repository.

## Rules

- Treat `manifests/` as package metadata, not application source.
- Never invent installer URLs, versions, SHA256 hashes, or package identifiers.
- Only add a manifest when a real Windows installer is published.
- Keep each pull request limited to one package/version update.
- Preserve official WinGet directory and filename conventions.
- Validate changed manifests before merging.

## Manifest layout

```text
manifests/<publisher>/<package>/<version>/
├── <publisher>.<package>.yaml
├── <publisher>.<package>.installer.yaml
└── <publisher>.<package>.locale.en-US.yaml
```

## Validation

```powershell
winget validate --manifest <path-to-version-folder>
```

Do not recursively scan a large manifest tree when investigating one package; inspect only the package path involved.
