# GitHub Rock WinGet workflow

This repository packages **released GitHub Rock Windows installers** for WinGet. It does not contain application source code.

## Before creating a manifest

A real GitHub Rock Windows installer must already exist in a public GitHub release.

Required information:
1. Exact GitHub Rock release URL.
2. Exact installer asset URL.
3. Exact package identifier.
4. Exact released version.
5. Supported architecture and installer type.
6. SHA256 of the exact installer asset.

Do not invent or reserve values for a future release.

## Manifest layout

Use the official WinGet structure:

    manifests/<publisher>/<package>/<version>/
    ├── <publisher>.<package>.yaml
    ├── <publisher>.<package>.installer.yaml
    └── <publisher>.<package>.locale.en-US.yaml

Follow the naming and schema requirements documented by [microsoft/winget-pkgs](https://github.com/microsoft/winget-pkgs/tree/master/doc/manifest/schema).

## Hash the installer

On Windows:

    (Get-FileHash .\GitHub-Rock-<version>.exe -Algorithm SHA256).Hash

The hash must correspond to the exact installer URL recorded in the manifest.

## Validate

    winget validate --manifest <path-to-version-folder>

Then perform an installation test:

    winget install --manifest <path-to-version-folder>

Verify that the installed application launches and the installed version matches the manifest.

## Pull request rules

- One package/version change per PR.
- Link the GitHub Rock release.
- Do not upload installers to this repository.
- Do not include application source code.
- Do not use placeholder URLs, hashes, versions, or package IDs.
- Keep unrelated formatting changes out of manifest PRs.

## CI

The repository workflow validates manifest directories on Windows using WinGet. Pull requests are checked before merge; pushes to `main` revalidate the repository when manifests or the workflow change.

If no manifests exist yet, CI exits successfully without pretending a package was validated.