<!-- Keep each PR focused on one package/version change. -->

## Description

Describe the manifest change and link the GitHub Rock release or issue.

## Checklist

- [ ] This PR changes only one package/version.
- [ ] The manifest follows the WinGet schema.
- [ ] `winget validate --manifest <path>` passes locally.
- [ ] The installer URL is publicly accessible and stable.
- [ ] The SHA256 hash was calculated from the exact installer referenced.
- [ ] The package version matches the published GitHub Rock release.
- [ ] No generated binaries or unrelated files are included.

## Release

- GitHub Rock release: <URL>
- Package identifier: <Publisher.Package>
- Package version: <Version>
