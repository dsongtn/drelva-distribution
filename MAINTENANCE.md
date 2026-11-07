# Distribution maintenance — Drelva Access preview

This repository intentionally hosts **only public Drelva gateway artifacts and public verification keys**. Private application packages, authentication state, passwords and signing keys must never be committed here.

## Release invariants

1. Build and test the same source revision for each target architecture.
2. Sign native RPMs and both Linux repository metadata formats with the appropriate publisher key.
3. Publish immutable version-specific packages and archives. **Never silently replace a published file's bytes.**
4. Generate a complete SHA-256 manifest for every release asset and sign that manifest.
5. Test clean native installation, version check and uninstall from the **public HTTPS endpoints**, not only local files.
6. Ensure public metadata mentions the real limitations: the private OAuth client/entitlement is not configured, Windows Authenticode is absent, macOS package is not notarized and Microsoft WinGet catalog submission is pending.

## Key security

The preview repository RSA-3072 fingerprint is:

```text
AF08 1091 2D6A 5166 E193 C21A 894F 3FED FC60 AE33
```

The publisher's private key is **not** stored in this public repository or in GitHub Actions secrets. Until the key has been moved to a properly protected signing environment, treat the repository as a development-preview feed. Never copy the private key to a public CI worker or into bootstrap installers.

APT clients should use per-source `Signed-By`. Fedora clients should keep `gpgcheck=1` and `repo_gpgcheck=1`.

## Expiration and servicing

The current APT Release metadata has a **60-day Valid-Until** period from its signing date. This is deliberate freeze protection: an unattended static repository will eventually be rejected by APT if updates are not published. The maintainer must re-index, update Valid-Until and re-sign before expiry. Do **not** disable APT's expiration check to keep a neglected repository working.

For a new release:
- Add the new DEB files under `docs/apt/pool/` and regenerate per-architecture Packages, compressed Packages and immutable by-hash indexes.
- Generate a new `dists/stable/Release` with valid hashes, current date and bounded Valid-Until; sign `InRelease` and `Release.gpg`.
- Add signed RPMs under `docs/rpm/`; rebuild RPM metadata and sign `repomd.xml.asc`.
- Publish the package manifests, then test public HTTPS APT and DNF installs in isolated clean machines before releasing to existing fleets.
- Update external Homebrew/Scoop SHA-pinned formulas **only after** the new immutable artifact URLs are live.
- Validate a new WinGet manifest with the installed Windows client before submitting a separate versioned PR to Microsoft's community repository.
- Retain signing-key rotation and revocation procedures. Stronger signing and notarization are prerequisites before promoting this feed to production.

## Boundaries

Public software discovery and package installation do **not** grant private application entitlements. Drelva only becomes a functional opt-in gateway once the identity server registers the OAuth public client and implements its protected `packages:read` approval endpoint. Private repositories must still verify every download authorization independently.
