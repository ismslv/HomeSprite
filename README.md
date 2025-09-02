# HomeSprite
Multiplatform retro desktop companion

### Requirements

I tested it on:

- MacOS Sequoia 15.5
- Windows 11
- Ubuntu 24.04

In theory, it should support:

- MacOS Arm (Apple Silicon)
- Windows 10, 11
- Linux x64
- Linux Arm

### How to install

#### Windows

Use .msi installer file

#### MacOS

Mount .dmg file and drag app icon to Applications.

> [!NOTE]
> App is unsigned, so on some systems you may have to take standard steps [like these](https://support.apple.com/guide/mac-help/open-a-mac-app-from-an-unknown-developer-mh40616/mac).

#### Linux

Run .AppImage

Some Linuxes (e.g., latest Ubuntu) restricts the use of sandboxes. To lift the restrictions:

```shell
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
```

> [!NOTE]
> Due to how some linuxes display tray menu, Linux version contains a special, compact version of the menu.
