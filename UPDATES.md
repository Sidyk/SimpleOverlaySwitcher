# Publishing updates

Default manifest:
`https://raw.githubusercontent.com/Sidyk/SimpleLayoutSwitcher/main/version.json`

The repository distributes the DLL directly, like Better Flags. The updater helper is embedded in the DLL.

## Release checklist

1. Increase project, assembly and file versions, and update the displayed UI version.
2. Build Release on Windows with SimHub references available.
3. Run the updater and disabled-state tests in the local tools directory.
4. Copy the built DLL into the publication directory.
5. Compute its SHA-256 with `Get-FileHash .\SimpleOverlaySwitcher.dll -Algorithm SHA256`.
6. Update version.json (version, downloadUrl, sha256, changelog), README and CHANGELOG.
7. Publish DLL and manifest together in one commit to main.
8. Verify the public manifest and downloaded DLL checksum.

The download URL must return the DLL, not a ZIP or HTML page. Use:
`https://raw.githubusercontent.com/Sidyk/SimpleLayoutSwitcher/main/SimpleOverlaySwitcher.dll?v=VERSION`

The assembly name must be `SimpleOverlaySwitcher`. Assembly version must match the manifest (1.0.1.0 for 1.0.1). Only newer versions are offered. A missing checksum allows manual download only.

The previous DLL is retained as `SimpleOverlaySwitcher.dll.backup` in the SimHub directory after a successful automatic update. Close SimHub before restoring it manually.

## Optional development override

An existing `PluginsData/Common/SimpleOverlaySwitcher/update-source.txt` inside SimHub overrides the default manifest. It must contain an HTTPS URL. An empty file disables checking. Normal users do not need this file.

## Verification scope

Version parsing, HTTPS validation, embedded-helper presence and disabled overlay actions are tested locally. A complete upgrade from an older release should also be tested in a separate SimHub installation before publishing future releases.
