<p align="center""><img src="https://img.itch.zone/aW1nLzIzMDEzMjkxLnBuZw==/original/9LqRE5.png" width="500px"/></p>

__Your desktop, but with a little magic.__

HomeSprite is a companion app that brings animated Sprites from TrinketOS to your Windows, macOS, or Linux desktop.
They live in your tray, wander around in their little frame, and can be any character that the community creates.

### Requirements

I tested it on:

- macOS Sequoia 15.5
- Windows 11
- Ubuntu 24.04

In theory, it should support:

- macOS Arm (Apple Silicon)
- Windows 10, 11
- Linux x64
- Linux Arm

### How to install

#### Windows

Run .msi installer file.

> [!NOTE]
> App is unsigned, so Windows will show you the warning screen — select "run anyway".

#### macOS

Mount .dmg file and drag app icon to Applications.

One-line command that will download the latest file, mount, install, remove dmg and run app:
```zsh
curl -sL $(curl -s https://api.github.com/repos/ismslv/HomeSprite/releases/latest | grep "browser_download_url.*\.dmg" | cut -d '"' -f 4) -o ~/homesprite.dmg && hdiutil attach ~/homesprite.dmg && cp -r /Volumes/HomeSprite*/HomeSprite*.app /Applications && hdiutil detach /Volumes/HomeSprite* && rm ~/homesprite.dmg && open /Applications/HomeSprite*.app
```

> [!NOTE]
> App is unsigned, so on some systems you may have to take standard steps [like these](https://support.apple.com/guide/mac-help/open-a-mac-app-from-an-unknown-developer-mh40616/mac).

#### Linux

Extract .tar.gz and run homesprite.
One-line commands that will download the latest file, extract it, chmod and run app:

__for x64__
```bash
curl -sL $(curl -s https://api.github.com/repos/ismslv/HomeSprite/releases/latest | grep "browser_download_url.*homesprite-[0-9]*\.[0-9]*\.[0-9]*\.tar\.gz" | cut -d '"' -f 4) | tar -xzf - -C ~ && cd ~/homesprite-* && chmod +x homesprite && ./homesprite
```

__for ARM__
```bash
curl -sL $(curl -s https://api.github.com/repos/ismslv/HomeSprite/releases/latest | grep "browser_download_url.*homesprite-[0-9]*\.[0-9]*\.[0-9]*-arm64\.tar\.gz" | cut -d '"' -f 4) | tar -xzf - -C ~ && cd ~/homesprite-* && chmod +x homesprite && ./homesprite
```

Some Linuxes (e.g., latest Ubuntu) restricts the use of sandboxes. To lift the restrictions:

```bash
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
```

On some systems, you may need to install fuse library.

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install libfuse2

# Arch/Manjaro
sudo pacman -S fuse2

# Fedora/CentOS
sudo dnf install fuse
```

On some systems you can see a warning `Exiting GPU process due to errors during initialization`. It is harmless and due to drivers. If you want to remove this warning, launch app with a `--disable-gpu` flag.

> [!NOTE]
> Due to how some distros display tray menu, Linux version contains a special, compact version of the menu.

## How to create your Sprite

First, open the [Matrix](https://trinketos.org/matrix/).

If you want to download some character, click on its card, and in the editor click the button "Export to .sprite".

If you want to create your own character, click the "New" card. Add your frames to the animations, enter name aand other data, and export the file in the same manner.

Frames should be:

- Square png files without background
- Black and white
- Preferably in pixel-art style
- 256×256 (or down to 48×48 if they are pixel perfect)
- With a little space around, but not too small

Then you can click "submit" button and send me the file, if you want it to be added to the Matrix gallery.

## How to remove character

- Open tray menu → Settings → "Open app folder".
- Remove needed character's folder
- Restart HomeSprite

## Speech

One of the main abilities of the Sprite is the ability to speak. You can create lines for a character when creating a new one in Matrix (only "greeting" type for now), also you can send any text to a "say" command (see Scripting).

Here is the list of tags that you can use inside of speech lines:

<table>
  <tr>
    <td>&ltbr&gt</td>
    <td>Makes a new line.</td>
  </tr>
  <tr>
    <td>&ltpause&gt</td>
    <td>Makes a 1s pause.</td>
  </tr>
  <tr>
    <td>&ltpause X&gt</td>
    <td>Makes a Xs pause.</td>
  </tr>
  <tr>
    <td>&lttrick&gt</td>
    <td>Character pauses a speech and makes a special move.</td>
  </tr>
  <tr>
    <td>&ltslow&gttext&lt&#47;slow&gt</td>
    <td>Text will be written slowly.</td>
  </tr>
  <tr>
    <td>&ltfast&gttext&lt&#47;fast&gt</td>
    <td>Text will be written fast</td>
  </tr>
  <tr>
    <td>&ltnotype&gt</td>
    <td>Text is output immediately, without typing effect. Disables all tags like pause, slow, fast. Should be put in the beginning.</td>
  </tr>
  <tr>
    <td>&ltnoclose&gt</td>
    <td>Does not close text bubble after typing. Useful for long texts. Should be put in the beginning.</td>
  </tr>
</table>

Example of speech text with multiple tags:

```
Luke!<trick>I am<slow>...</slow> your father!<pause><br><fast>Nooooooooo!</fast>
```

## Scripting

You can use command line to call Sprite from your scripts. Only these commands are available in the first version: __say__, __sleep__, __wake__.

```bash
<path_to_homesprite_executable> say "Greetings!"
<path_to_homesprite_executable> sleep
<path_to_homesprite_executable> wake
```

