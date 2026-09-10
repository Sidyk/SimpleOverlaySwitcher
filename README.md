# Simple Overlay Switcher

**Switch overlays while driving.**

A Windows SimHub plugin by **Sidyk** for switching between complete saved overlay layouts with your steering wheel, button box or keyboard.

**[Download SimpleOverlaySwitcher.dll](https://raw.githubusercontent.com/Sidyk/SimpleLayoutSwitcher/main/SimpleOverlaySwitcher.dll?v=1.0.1.1)**

Current version: **1.0.1.1** — [Changelog](CHANGELOG.md)

## Features

- Rotate complete layouts from Dash Studio's **Saved Overlay Layouts**, for example LMP → GT3 → LMP.
- Add or remove layouts and arrange their rotation order.
- Bind Next and Previous directly in the plugin's **Button Mapping** section.
- Assign a game to each layout and enable automatic loading.
- Keep the layout's saved positions, sizes and overlay settings.
- Receive a notification when an update is available and install it with **Update & Restart**.

This plugin switches saved layouts, not individual entries from Available Overlays. It does not rewrite your layout files.

## Installation

1. Download **SimpleOverlaySwitcher.dll** using the link above.
2. Close SimHub.
3. Copy the DLL into your SimHub installation folder, usually `C:\Program Files (x86)\SimHub`.
4. If Windows blocked the download, right-click the DLL, choose **Properties**, then **Unblock**.
5. Start SimHub and enable the plugin if prompted.
6. Open **Simple Overlay Switcher** in the sidebar and check **Switcher enabled**.

Built for .NET Framework 4.8 and tested against SimHub **9.11.9**. Future SimHub versions may require compatibility updates because saved-layout loading uses internal SimHub APIs.

## Setup

1. Create and save your layouts in Dash Studio → **Saved Overlay Layouts**.
2. Enable the switcher, then click **Refresh layouts**.
3. Add the desired layouts to **Rotation Order** and use ↑ / ↓ to arrange them.
4. Under **Button Mapping**, click a mapping and bind your preferred input.
5. Use **Next Overlay Layout** or **Previous Overlay Layout** while driving.

Rotation wraps around. The native actions `SimpleOverlaySwitcher.NextOverlay` and `SimpleOverlaySwitcher.PreviousOverlay` are also available in SimHub's Controls and events.

## Automatic loading per game

Choose **Settings** beside a layout in the rotation, select a game under **Auto-load for game**, then check **Enable auto load**.

The layout loads when SimHub reports the game starting or changing. It is not continuously forced, so you can still change layouts manually. Changing an assignment or enabling autoload can also apply it to the current game. If multiple layouts target the same game, the first matching layout in the rotation wins.

## Main switch

When **Switcher enabled** is unchecked, rotation, mapped actions, autoload and update checks/downloads are inactive. Configuration controls are disabled. Your saved configuration is retained and the currently displayed SimHub layout is left untouched.

## Automatic updates

The plugin checks this repository's [version.json](version.json) when enabled. When a newer version is found, a popup offers an update; the settings page also displays **Update & Restart**.

After confirmation, the plugin downloads the DLL, verifies its SHA-256 checksum and assembly identity/version, asks for Windows administrator permission, closes SimHub, installs the update and restarts SimHub. The updater helper is embedded in the DLL: no additional installer is needed.

Settings and button mappings are preserved. An unavailable update server does not prevent layout switching. For publishing instructions, see [UPDATES.md](UPDATES.md).

## Troubleshooting

- **No layouts listed:** save them in Saved Overlay Layouts, enable the switcher, then refresh.
- **Buttons do nothing:** ensure the switcher is enabled and at least two available layouts are in the rotation; check the mappings.
- **Autoload does not run:** both checkboxes must be enabled and the layout must be assigned to the correct game.
- **Wrong overlay position:** edit and save the original layout in SimHub.
- **Update status: Unknown:** check your Internet connection and try again after restarting SimHub.
- **Other issues:** look for `[SimpleOverlaySwitcher]` in SimHub's logs.

## Support

Created by **Sidyk**.

[Support via PayPal](https://www.paypal.com/paypalme/MrSIdyk)
