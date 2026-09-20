# WinGet package workflow

## 1. Publish

GitHub Rock must first publish a real Windows installer through a GitHub release.

## 2. Create the manifest

Create the package directory using the exact WinGet package identifier and version.

## 3. Calculate the installer hash

```powershell
(Get-FileHash .\GitHub-Rock-<version>.exe -Algorithm SHA256).Hash
```

## 4. Validate

```powershell
winget validate --manifest <path-to-version-folder>
```

## 5. Test

Install from the local manifest and verify that the installed application launches correctly.

## 6. Pull request

Keep the PR focused on one package/version. Include the release URL and validation result.

> No placeholder manifests are allowed. A real installer, release URL, version, and SHA256 are required before the first package is added.
