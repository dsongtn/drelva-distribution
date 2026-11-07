# Drelva Access — Public Distribution (Preview)

**Public, credential-free gateway binaries and native package feeds only.** Private applications, Forgejo packages, access tokens, backend code and signing secrets are NOT in this repository.

> Current status (November 2026): Drelva `0.1.1` installs and `drelva doctor` checks the public identity server. Full `drelva join` remains **disabled** until its public OAuth client ID and server-side `packages:read` entitlement endpoint have been provisioned. Do not mistake a package installation for granted access.

This is a small opt-in client, not another package manager. Public distribution uses existing OS tools; authentication is performed at the owner's identity server and private software access requires separate explicit approval.

## Install through native package sources

See the [installation site](https://dsongtn.github.io/drelva-distribution/) for exact copyable steps and the **preview GPG signing-key fingerprint**.

- **Debian/Ubuntu:** import the independently verified public repository key and install the `drelva.sources` file. Then `sudo apt update && sudo apt install drelva`.
- **Fedora:** install the `drelva.repo` source using DNF5 and approve the verified package signing key. Then `sudo dnf install drelva`.
- **Windows:** a per-user, unattended-capable Inno Setup installer is available in Releases. A WinGet community manifest is prepared separately, but public catalog availability requires Microsoft review.
- **macOS:** a separate public third-party Homebrew tap provides the portable executable. Homebrew itself is not preinstalled. Apple Developer ID notarization is not available for this preview.

Current platform packages contain no password, package registry credentials, privileged code, injected services or auto-start tasks. They install only the opt-in CLI and documentation.

## Preview repository key

**Fingerprint (RSA-3072, expires November 2027):**

```text
AF08 1091 2D6A 5166 E193 C21A 894F 3FED FC60 AE33
```

This is a **preview key**, stored on the development workstation and separate from this public GitHub repository. Package and repository signatures have been validated using isolated APT/DNF installation tests. For production, use hardware-backed or otherwise better protected signing with documented rotation; a private key on an online development machine is not a production trust root.

Never add the signing key globally with `apt-key` or disable `gpgcheck` to bypass verification. Use only a scoped `Signed-By` APT key and DNF's standard `gpgcheck=1` + `repo_gpgcheck=1`.

## Releases and limitations

[Public gateway release](https://github.com/dsongtn/drelva-distribution/releases/tag/v0.1.1). Versioned files have SHA-256 checksums. Windows installer is not Authenticode-signed; macOS Developer ID notarization is not complete. Marketplace acceptance is **not** claimed.

Our proprietary development source lives in a separate **private** GitHub repository. The public gateway is deliberately thin. Its name is provisional, and a full brand/trademark clearance has not been performed.
