# Gameque Releases

Official Gameque installers and update metadata.

This repository is **distribution only**. It holds no source code, history,
issues or development files — just one GitHub Release per official version.

Each release carries exactly three files:

| File | What it is |
|---|---|
| `Gameque-<version>-setup.exe` | The Windows installer |
| `Gameque-<version>-setup.exe.sha256` | Its SHA-256, in `sha256sum` format |
| `release.json` | Version, tag, source commit, installer name, size and checksum |

Installed copies of Gameque read these releases anonymously to find updates, and
refuse any installer whose SHA-256 does not match `release.json`.

The files are built and verified by Gameque's own release pipeline and uploaded
here unchanged; nothing is built in this repository.

## Verifying a download

```powershell
(Get-FileHash .\Gameque-0.8.2-setup.exe -Algorithm SHA256).Hash.ToLower()
```

Compare the result with the first field of the matching `.sha256` file.
