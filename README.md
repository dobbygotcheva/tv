# tv

A small helper script to cast your Linux laptop screen to a Miracast TV using
[GNOME Network Displays](https://flathub.org/apps/org.gnome.NetworkDisplays).

Tested on Ubuntu 24.04 (GNOME, Wayland) with an LG webOS TV.

## What it does

- Installs Flatpak remote (Flathub) and the app if they are missing (user-level, no `sudo`)
- Makes sure Wi-Fi is on and a Wi-Fi P2P device exists
- Starts the app and cleans up on `Ctrl+C`
- Can reset a stuck instance

## Requirements

- Linux with GNOME, NetworkManager and a Wi-Fi card that supports Wi-Fi Direct (P2P)
- `flatpak` (`sudo apt install flatpak`)
- A TV with Miracast / Screen Share enabled

## Install

```bash
mkdir -p ~/.local/bin
cp tv ~/.local/bin/tv
chmod +x ~/.local/bin/tv
```

Make sure `~/.local/bin` is in your `PATH`.

## Usage

```bash
tv            # start casting
tv --reset    # kill a stuck instance, reset P2P state, then start
tv --stop     # stop the app
tv --status   # show Wi-Fi / P2P / app status without casting
tv --logs     # start with debug logs in /tmp/tv-debug.log
tv --help
```

On the TV, open **Screen Share / Miracast** and keep that screen open, then pick
the TV from the list in the app.

## Troubleshooting

- The version from Ubuntu's `apt` (0.92.1) can fail to start streaming; the
  Flatpak version (0.99+) works, which is what this script uses.
- If running `tv` shows no window, an old instance may be running: `tv --reset`.
