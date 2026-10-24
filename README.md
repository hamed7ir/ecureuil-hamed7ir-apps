# ecureuil-hamed7ir-apps

This is my source for [Ecureuil](https://github.com/fraaaaa4/ecureuil), the app store for Windows RT made
by fratta. It lists my apps for Windows RT and ARM32 Windows. I made and tested them on a Surface RT and a
Surface 2. Some of them run on normal x86 and x64 Windows too.

This repo doesn't host the downloads. It's just JSON on GitHub Pages. Ecureuil reads it and downloads
each app from its own GitHub release.

## What's in it

8 apps, 10 entries. DroidFinestra and Venetium have a separate ARM32 build and a separate x86 / x64
build, so each of them is two entries.

| App | Version | Category | Architecture | Runs on |
|---|---|---|---|---|
| [Finestra](https://github.com/hamed7ir/Finestra): RDP, SSH, SFTP, FTP and FTPS client | 2.0.0 | Utilities | neutral | RT 8.0, RT 8.1, Windows 10 ARM32, x86 / x64 Windows 10 and 11 |
| [TelegArm](https://github.com/hamed7ir/TelegArm): Telegram client with calls | 2.0.0 | Utilities | neutral | RT 8.0, RT 8.1, Windows 10 ARM32, Windows 8.1 to 11 (x86, x64, ARM64), Windows 7 without calls |
| [CS-Ray](https://github.com/hamed7ir/CS-Ray): proxy client (VLESS, REALITY, VMess, Shadowsocks) | 2.0.0 | Utilities | neutral | RT 8.0, RT 8.1, Windows 10 ARM32, x86 / x64 Windows 7 to 11 |
| [Venetium](https://github.com/hamed7ir/venetium): Chromium 150 browser | 1.2 | Utilities | arm32 | Windows 10 ARM32 (build 15035) |
| [Venetium (x86)](https://github.com/hamed7ir/venetium): the same browser, x86 build | 1.2 | Utilities | x86-32 | Windows 10 and 11 |
| [DroidFinestra](https://github.com/hamed7ir/DroidFinestra): use your Android phone from Windows (scrcpy GUI) | 1.0.0 | Utilities | arm32 | RT 8.0, RT 8.1, Windows 10 ARM32 |
| [DroidFinestra (x64)](https://github.com/hamed7ir/DroidFinestra): the same app, x64 build | 1.0.0 | Utilities | x86-64 | 64-bit Windows 10 and 11 |
| [Xtreme Download Manager](https://github.com/hamed7ir/xdm): download manager, my fork of [subhra74/xdm](https://github.com/subhra74/xdm) | 8.0.29-rt1 | Utilities | arm32 | RT 8.0, RT 8.1, Windows 10 ARM32 |
| [Lite XL](https://github.com/hamed7ir/lite-xl-rt): text editor, my ARM32 build of [lite-xl](https://github.com/lite-xl/lite-xl) | 2.1.8-arm32 | Development | arm32 | RT 8.0, RT 8.1, Windows 10 ARM32 |
| [Varan](https://github.com/hamed7ir/varan): web browser, my fork of [Pale Moon](https://www.palemoon.org/) | 1.1 | Utilities | arm32 | RT 8.0, RT 8.1, Windows 10 ARM32 |

**neutral** means one download works on every architecture. Finestra, TelegArm and CS-Ray are AnyCPU
.NET apps, so each of them is one entry, and Ecureuil shows it as compatible on any PC.

If a project also has a portable zip, you find it on that project's release page. This list only has
the installers.

## How to add it in Ecureuil

It's in **Discover Sources**. You can also add it by hand: open the **Sources** tab and paste this:

```
https://hamed7ir.github.io/ecureuil-hamed7ir-apps/sources.json
```

Ecureuil keeps a source for 24 hours before it checks again. After I update the list, press **Refresh**
in the source details if you want to see it right away.

## Before you install

Some of these apps need things that I can't put in the download:

- **Windows RT** only runs unsigned desktop apps after a jailbreak.
- **Finestra, TelegArm and CS-Ray** need **.NET Framework 4.7** or newer. Windows RT 8.1 comes with 4.5,
  so install 4.7 first. On **RT 8.0** you need the **.NET Framework 4.8 update**, and it's hard to find
  for RT 8.0 right now.
- **TelegArm** calls need Windows 8.1 or newer.
- On **Windows 7**, CS-Ray only works in system proxy mode, because its full tunnel uses the Wintun
  driver and that needs Windows 8. TelegArm on Windows 7 needs the Visual C++ 2015 or newer
  redistributable (x86) for animated stickers, and calls don't work there.
- **DroidFinestra** needs **USB debugging** turned on, on the phone. Pick the build for your PC: ARM32
  for Windows RT and ARM32 Windows, x64 for 64-bit Windows 10 and 11.
- **Venetium** for ARM32 needs Windows 10 build 15035. Windows RT 8.0 and 8.1 are not supported yet.
- **XDM** needs **WPF for ARM32**. It's Microsoft's, so I can't share it here.
- **Varan** needs the **Microsoft Visual C++ 2015 or newer redistributable for ARM32**, and YouTube in
  Varan needs the vorapis extension.
- **Varan** and **XDM** need the device in **test-signing mode**.
- **Lite XL** needs nothing. Only its installer uses .NET Framework 4.0, and Windows RT already has it.

Every entry has its own install steps. Read them in Ecureuil before you install.

## How the list is made

```
sources.json                        the source record, Ecureuil reads this first
hamed7ir/*.json                     one file per installer
source-name-index.json              made by .github/workflows/build-catalogs.yml, the bot commits it
```

Don't edit `source-name-index.json` by hand. The workflow builds it again from `hamed7ir/*.json` every
time something in that folder changes.

## If something is wrong

Open an issue **here** if the list is wrong: a bad size, a dead download, wrong install steps, a missing
requirement, or the wrong Windows versions.

Open an issue in the **app's own repo** (linked in the table) if the app itself has a problem. For XDM,
Lite XL and Varan, please don't report ARM32 problems to the original projects. They don't make ARM32
builds.

## Credits

[Ecureuil](https://github.com/fraaaaa4/ecureuil) and its source format are made by **fratta**
([@fraaaaa4](https://github.com/fraaaaa4)). This repo uses the same layout and the same
`build-catalogs.yml` as his [Ecureuil-fratta-apps](https://github.com/fraaaaa4/Ecureuil-fratta-apps).

XDM is made by **Subhra Das Gupta**. Lite XL is made by the **Lite XL Team** and comes from rxi's lite.
Varan is a fork of **Pale Moon** by Moonchild Productions, and they don't make or support it. Venetium is
built on **Supermium** and **ungoogled Chromium**. DroidFinestra starts **scrcpy** by Genymobile and
doesn't change it. Each entry credits the original authors too.
