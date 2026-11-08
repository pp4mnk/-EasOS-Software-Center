# -EasOS-Software-Center

ENGLISH AND SPANISH EDITGION   (EN-English, the other file with no mark....SPANISH)  ...by pp4mnk


**Discover, install and manage software on EasyOS from one graphical interface.**

Easy Software Center brings together a searchable native package catalogue, a selection of popular applications, a built-in AppImage manager and shortcuts to EasyOS software tools. Its goal is to make finding and installing software easier, with clear application details and installation confirmations.

## Features

- **Full local APT catalogue:** browse the packages available in your configured repositories.
- **38 featured applications:** discover popular software for browsing, office work, graphics, multimedia, education, development and more.
- **Search and category filters:** find packages by name, description, identifier or category, with 40 results per page.
- **Double-click installation workflow:** prepare a native package installation, review dependencies and proposed changes, then click **Install**.
- **Package index refresh:** update repository information without performing a general application upgrade.
- **Application details:** access descriptions, official websites and user forums where identified, with visible links you can copy.
- **AppImage management:** download selected GitHub releases, import local files, launch, update, remove and restore a previous version.
- **EasyOS manager shortcuts:** open PKGget, SFSget, Appi and Flapi when available.
- **Local package handling:** send supported package files to the appropriate EasyOS workflow.
- **English interface:** supplied interface text, help and documentation are in English.

## Requirements

- EasyOS 7.x; the package metadata targets Excalibur.
- Python 3.8 or newer.
- PyGObject (`python3-gi`) and GTK 3 (`gir1.2-gtk-3.0`, or the equivalent packages in your edition).
- APT and configured repositories for the native catalogue and direct native installation.
- Administrator privileges for native package installation and index updates.
- Linux **x86_64** for the built-in AppImage installer.
- Internet access for downloads, repository updates and external links.

There are no pip dependencies. PKGget, SFSget, Appi, Flapi and `petget` must be present to use their respective integrations.

## Installation

1. Download `easy-software-center-0.3-en.pet` from this repository wherever the maintainer provides the package.
2. Close any running instance of Easy Software Center.
3. Double-click the PET file in EasyOS and accept installation.
4. Open **Menu → Utility → Easy Software Center**. The exact menu placement may vary.
5. Save your EasyOS session if your current operating mode requires it to retain changes after rebooting.

You can also launch the program from a terminal:

```sh
easy-software-center
```

If a dependency message appears, install Python 3, PyGObject and GTK 3 using PKGget, then launch the program again.

## Using the catalogue

Choose a source:

| Source | Contents |
| --- | --- |
| **Featured** | 38 selected applications, with useful project links and available installation options. |
| **Native packages** | The full local APT index for your configured repositories. |
| **Installed · ESC AppImages** | AppImages installed or imported through this software centre. |

Enter a search term, choose a category and browse the results. Click an entry to see its details and available actions.

**Reload catalogue** rereads the existing local APT index. **Update index** refreshes information from your configured repositories and then reloads the catalogue. Updating the index does not install or upgrade applications.

### Installing native packages

Double-click a native entry, or select it and choose **Install package**. The program first asks APT to simulate the installation. Review the proposed dependencies and changes, then click **Install** to proceed.

The installation uses APT with `--no-remove`, which blocks plans requiring package removal, and preserves existing configuration files when dpkg would otherwise ask about replacements. Dependencies and upgrades required by the selected installation can still be included in the plan.

Use **Manage in PKGget** for the separate package-manager workflow. The selected package name is copied to the clipboard for pasting into its search field.

### Managing AppImages

For selected featured applications, choose **Download GitHub AppImage**. The program checks the project's latest GitHub release for a suitable AppImage and shows the version, file, size and download source before installation.

Use **Local file…** to import an existing x86_64 AppImage. Installed AppImages appear under **Installed · ESC AppImages**, where you can launch or remove them. GitHub-backed entries also offer updates. When replacing an installed AppImage, the previous executable and metadata are retained so you can choose **Restore previous AppImage**.

The installer validates the AppImage header and x86_64 architecture, calculates SHA-256 and checks it against the published digest when a SHA-256 digest is supplied by GitHub. A calculated checksum alone does not verify the publisher. Applications are not launched automatically during installation.

Restoring a previous AppImage restores its executable and installation metadata; it does not restore application documents or settings.

### Opening local files

| File type | Behaviour |
| --- | --- |
| `.AppImage` | Imports a supported x86_64 AppImage into the built-in manager after confirmation. |
| `.pet`, `.deb`, `.rpm`, `.tar.xz` | Passes the selected file to `petget` after confirmation. Actual support and compatibility depend on EasyOS and the package. |
| `.sfs` | Shows instructions to select the file in Easy BootManager under the Filesystem menu. |
| `.flatpakref`, `.flatpak` | Opens Flapi and asks you to import the file there. |

The top toolbar also provides direct access to **PKGget**, **SFSget**, **Appi** and **Flapi**. Their catalogues and installation operations remain in those managers.

## Featured software

The 38 featured entries include Firefox, Chromium, Thunderbird, VLC, GIMP, LibreOffice, Blender, Scribus, OBS Studio, mpv, Audacious, FileZilla, Transmission, Geany, Git, GParted, Syncthing, Calibre, Stellarium, GCompris, Tux Paint, Scratch, SuperTuxKart, Battle for Wesnoth, BleachBit, Remmina, KeePassXC, Krita, Shotcut, Kdenlive, FreeCAD, Inkscape, Obsidian, Joplin, LocalSend, QOwnNotes, balenaEtcher and Audacity.

A featured entry is a discovery aid: its presence does not guarantee that a native package or a compatible GitHub AppImage is available.

## Files and data

| Location | Purpose |
| --- | --- |
| `/usr/local/bin/easy-software-center` | Launcher and dependency check. |
| `/usr/local/lib/easy-software-center/center.py` | Python application. |
| `/usr/share/applications/easy-software-center.desktop` | System menu entry. |
| `/usr/share/doc/easy-software-center/README.txt` | Bundled documentation and MIT license text. |
| `~/.local/share/easy-software-center/` | Managed AppImages, metadata, icon cache and logs. |
| `~/.local/share/applications/esc-*.desktop` | Menu launchers for managed AppImages. |

The English edition uses the same AppImage storage locations as the Spanish 0.3 edition. Its installer backs up a recognised older user-level menu entry from the shell-script edition with the suffix `.before-pet` before removing that duplicate entry.

## Limitations and troubleshooting

- **Catalogue size varies:** results depend on your configured repositories and the freshness of the local index. Libraries, documentation and command-line tools are included, so not every entry launches a graphical application.
- **APT unavailable:** use PKGget for your edition. The program falls back to its featured catalogue when no native entries are loaded.
- **No suitable GitHub AppImage:** the latest release may not contain one. Use the application's official website for other download options.
- **An AppImage will not start:** check its `launch.log` inside its folder under `~/.local/share/easy-software-center/`. FUSE or additional dependencies may be required. The program does not automatically disable application sandboxing.
- **Native installation fails:** inspect the corresponding `apt-<package>.log` in the software centre's data directory.
- **Website does not open:** copy the displayed URL and open it manually. Browser launch errors are recorded in `browser.log` in the same data directory.
- **A manager shortcut is unavailable:** that tool may be absent from your EasyOS edition.

External packages and AppImages are not certified for every EasyOS release. This English edition is intended for international EasyOS users; compatibility with other Linux distributions or CPU architectures is not guaranteed. Third-party websites, managers and applications retain their own language settings.

The package's bundled documentation records syntax, integrity, translation and core-logic checks, but no installation or visual testing in a live EasyOS session in its build environment.

## Uninstalling

Remove **Easy Software Center** through PKGget. User AppImages and data are retained.

To remove an AppImage managed by the centre, select it and choose **Remove AppImage**. This removes its managed executable, retained previous version, associated installation metadata and menu launcher. Application documents and preferences stored elsewhere are kept.

## Reporting issues

When reporting a problem in this repository's issue tracker, include your EasyOS version, CPU architecture, the application or package involved, the steps to reproduce it and the relevant error or log excerpt. Remove personal information before posting logs.

## License

Easy Software Center is distributed under the **MIT License**.

Copyright © 2026 pp4mnk. The full license text is included in the PET package's `README.txt`. Third-party applications and logos retain their respective licenses.

---

**Easy Software Center 0.3 · …by pp4mnk**
