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

```shell
<path_to_homesprite_executable> say "Greetings!"
<path_to_homesprite_executable> sleep
<path_to_homesprite_executable> wake
```

