# OsterSea Updates

Official installers and signed updates for **OsterSea Vessel Operations**.

> This repository is public and contains distribution files only. The OsterSea source code, operational databases, license files, customer data, and private keys are not stored here.

## Isolert lokal webapp v0.0.3

[Last ned v0.0.3-testpakken](https://github.com/hm4zp8g6np-code/OsterSea-Updates/releases/tag/v0.0.3-isolated.1) og se [installasjonsveiledningen](docs/v0.0.3-isolated.1.md). Dette er en separat, usignert prerelease for isolerte testdata. Automatisk oppdateringssjekk skjer uten innlogging i egen testkanal; den eksisterende signerte latest.json-kanalen og eldre installasjoner endres ikke. Faktisk overtakelse av skriverett er fortsatt sperret.

## Current status

No production release is published yet. The root [`latest.json`](latest.json) intentionally contains `"release": null`, so an OsterSea installation must treat the channel as having no available update.

## Planned packages

GitHub Releases will contain separate signed installers:

- `OsterSea_Standalone_Setup_vX.Y.Z.exe`
- `OsterSea_Server_Setup_vX.Y.Z.exe`
- `OsterSea_Client_Setup_vX.Y.Z.exe`

Release assets are used both for first-time installation and for automatic updates. Offline installation of the same signed package remains supported.

## Update safety

Before OsterSea installs an update, it must verify:

1. The manifest signature from the dedicated update-signing key.
2. The requested product: STANDALONE, SERVER, or CLIENT.
3. The downloaded file's SHA-256 value.
4. The Windows publisher signature when production code signing is enabled.
5. A complete verified backup before replacing program files.
6. Health checks after installation, with automatic rollback on failure.

Release signing and license signing are separate trust systems. See [the publishing policy](docs/PUBLISHING.md).
