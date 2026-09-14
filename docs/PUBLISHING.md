# Publishing OsterSea releases

This public repository is a distribution endpoint only. OsterSea source code remains in the private source repository.

## Allowed content

- Signed Windows installers for STANDALONE, SERVER, and CLIENT
- `latest.json`
- Release notes
- SHA-256 values and release signatures
- Public verification keys when the update-signing design is approved

## Content that must never be published

- Source code or Developer builds
- Vessel databases, documents, reports, configuration, logs, or backups
- Activation requests, issued license files, or the license registry
- Private signing keys, passwords, tokens, or credentials
- Customer, crew, cargo, voyage, or installation data

## Release gate

A release may be promoted to `stable` only after all of these checks pass:

1. Build from an approved commit in the private source repository.
2. Confirm that the package contains no database, license, key, test-vessel, or source files.
3. Run malware scanning and the OsterSea installation health check.
4. Calculate SHA-256 for every installer.
5. Sign the installer and the manifest with the dedicated update-signing key.
6. Upload installers as GitHub Release assets.
7. Publish release notes.
8. Update `latest.json` last.
9. Test online update, offline installation, backup, health check, and rollback.

The update-signing key must be separate from the license-signing key.

## Failure safety

If the manifest is missing, invalid, unsigned, or references a hash that does not match the downloaded file, OsterSea must refuse installation and continue using the current version.
