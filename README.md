# GameBoost

A native GTK4/libadwaita app for Ubuntu 26.04 (GNOME 50) that switches the whole desktop between three profiles with one click:

- **macOS** — MacTahoe-Dark GTK theme, glass pill top bar, rounded floating dock, blue folders, slate accent
- **Windows** — grey full-width bottom taskbar, no top bar, Windows-logo Start, Microsoft Store icon, Win11 icons
- **Ubuntu** — stock Ubuntu Dock on the left, Yaru-dark, orange accent

It also has a **Fan control** section that reads the HP WMI hwmon interface and lets you switch between Auto (BIOS-managed) and Max, with a manual PWM slider if your driver exposes `pwm1`/`fan1_target`. Writes go through `pkexec`.

## Installation

```bash
git clone https://github.com/Grant-1maker/gameboost.git
cd gameboost
install -Dm755 gameboost ~/.local/bin/gameboost
```

Then launch it from the app menu or with `~/.local/bin/gameboost`.

GameBoost expects the matching assets from the companion [`desktop-profiles`](https://github.com/Grant-1maker/desktop-profiles) repo to be installed. See that repo's README for the full setup.

## What it changes

Each profile sets: enabled/disabled shell extensions, dock position and styling, GTK theme, icon theme, accent colour and wallpaper. Windows mode writes a CSS block into Liquid Glass to hide the top bar; Ubuntu mode keeps Liquid Glass loaded as a CSS loader so a stylesheet override can square off the Ubuntu Dock corners. Dash to Panel settings are never written — those are left to the user's own tuning.

## Requirements

- GNOME Shell 50 / Ubuntu 26.04
- Python 3 with `python3-gi`, `gir1.2-gtk-4.0`, `gir1.2-adw-1`
- `gsettings`, `gnome-extensions` CLI
- Companion extensions and assets from `desktop-profiles`

No GDM or login-screen changes are made.

## License

MIT — see `LICENSE`.
