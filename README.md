# Drelva

Drelva is a small cross-platform command-line utility. This repository contains its platform packages, repository metadata, and versioned downloads.

## Installation

Full installation instructions: **https://dsongtn.github.io/drelva-distribution/**

| Platform | Package source | Command after initial setup |
| --- | --- | --- |
| Fedora | DNF5 repository | `sudo dnf install drelva` |
| Debian / Ubuntu | APT repository | `sudo apt install drelva` |
| Windows | [Versioned installer](https://github.com/dsongtn/drelva-distribution/releases/tag/v0.1.1) or [Scoop bucket](https://github.com/dsongtn/scoop-drelva) | `scoop install drelva` (if Scoop is installed) |
| macOS | [Homebrew tap](https://github.com/dsongtn/homebrew-drelva) | `brew tap dsongtn/drelva && brew install drelva` |

## Version

`0.1.1` is a development preview. Run `drelva version` and `drelva doctor` to check the installation. Other commands may not be available in this build.

Windows and macOS native installers in this release are not digitally signed/notarized. Use the versioned checksums when checking downloads.

## Repository key

APT and DNF packages are published with a preview signing key. Independently compare its fingerprint before installing:

```text
AF08 1091 2D6A 5166 E193 C21A 894F 3FED FC60 AE33
```

The corresponding verification key is available at [keys/drelva-preview.asc](https://dsongtn.github.io/drelva-distribution/keys/drelva-preview.asc).

These repositories are not the Microsoft Store, WinGet community source, or Apple's App Store. Availability through those catalogs is separate.
