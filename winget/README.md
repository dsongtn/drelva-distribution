# Draft Windows Package Manager (WinGet) community manifest

The proposed ID is `Drelva.DrelvaAccess`. This is a **validated local manifest candidate only**, not a registered WinGet community package. `winget install Drelva.DrelvaAccess` does not work from the Microsoft community source until its submission has been reviewed and accepted.

- Public Inno Setup installer: `DrelvaAccess-0.1.1-Windows-x64-setup.exe`
- Per-user installation and complete uninstall tested on Windows 11, including PATH restoration.
- Native Authenticode **NotSigned**. This release is a preview; public submission/certification and signing are still pending.
- Build currently performs `doctor` and a server-controlled opt-in handshake; the OAuth client and private entitlement server endpoints are not yet enabled.

For testing with `winget validate --manifest` use the three YAML files under `manifests/d/Drelva/DrelvaAccess/0.1.1/`. Local-manifest installation requires the user's explicit WinGet setting; do not enable it silently.

Do not represent this draft as a Microsoft Store listing.
