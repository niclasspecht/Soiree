# Soiree

<p align="center">
  <strong>A Discord-styled Windows build of <a href="https://github.com/ViceVerse-cz/Serein">Serein</a>, the lightweight native Discord client written in Rust.</strong>
</p>

<p align="center">
  <a href="https://github.com/niclasspecht/Soiree/releases"><img src="https://img.shields.io/github/v/release/niclasspecht/Soiree?label=release&color=5865F2" alt="Release" /></a>
  <img src="https://img.shields.io/badge/platform-Windows-informational.svg" alt="Platform: Windows" />
  <a href="LICENSE-MIT"><img src="https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-green.svg" alt="License: MIT or Apache-2.0" /></a>
</p>

*Serein* is French for the soft rain that falls on a clear evening. *Soiree* is that evening.
It is the same fast native client, tuned to look and sound like the Discord you know.

---

> [!WARNING]
> **Unofficial and not endorsed by Discord or by the Serein project.**
> Like Serein, Soiree talks directly to Discord's gateway and REST endpoints with your own
> account. Using third-party clients on normal accounts violates Discord's Terms of Service
> and can get your account terminated. Use at your own risk; trying it on a secondary account
> first is a good idea.

## What Soiree changes

| | Serein | Soiree |
|---|---|---|
| Default look | Serein's own dark/light palette, azure accent | Classic Discord greys (`#1E1F22` / `#2B2D31` / `#313338`) and Discord light theme, blurple accent (`#5865F2`) |
| Sound effects in calls | Always on the Windows default output device | On the output device you selected for voice, falling back to the default (fixes inaudible join/leave cues on headsets) |
| Updates | From Serein releases | From [Soiree releases](https://github.com/niclasspecht/Soiree/releases) only |
| Data and login | `%LOCALAPPDATA%\serein`, keyring `cz.viceverse.serein` | `%LOCALAPPDATA%\soiree`, keyring `Niclas.Soiree`, so Soiree runs side by side with Serein |
| Platforms | Windows, macOS, Linux | Windows (x64 and ARM64) |

Everything else (voice, screen share, extensions, performance) is Serein. Internal crate and
executable names (`serein.exe`) are unchanged to keep merging upstream changes simple.

### Optional theme

[`themes/discord-classic.serein-extension`](themes/discord-classic.serein-extension) also matches
Discord's font sizes, spacing and corner radii. Import it in **Settings > Themes**.
`Ctrl+Shift+F12` resets any theme.

## Download

Grab `soiree-vX.Y.Z-Windows-X64-Setup.exe` (or the `.zip` for a portable copy) from the
[latest release](https://github.com/niclasspecht/Soiree/releases/latest). ARM64 builds are
named `...-Windows-ARM64...`.

The builds are **not code-signed**, so Windows SmartScreen may show "Windows protected your PC"
on first start. Choose *More info > Run anyway* if you trust this repository. Every release
lists SHA-256 checksums in `SHA256SUMS.txt`.

## Build from source

Requires the pinned Rust toolchain (installed automatically by `rustup` from
`rust-toolchain.toml`) and, for the installer, [NSIS](https://nsis.sourceforge.io/).

```sh
cargo xtask package
```

The app ends up in `dist/`, the installer in `dist-installer/`.

## Releasing (maintainer)

Run the **Release** workflow from the Actions tab with a version such as `1.0.0`. It builds
Windows x64 and ARM64, creates the installer and zip, writes `SHA256SUMS.txt` and publishes
the GitHub release that the in-app updater checks.

## Staying in sync with Serein

```sh
git remote add upstream https://github.com/ViceVerse-cz/Serein
git fetch upstream
git merge upstream/main
```

## Credits and licenses

Soiree is a fork of [Serein](https://github.com/ViceVerse-cz/Serein) by its contributors and is
distributed under the same terms: [MIT](LICENSE-MIT) OR [Apache-2.0](LICENSE-APACHE). See
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md). The bundled notification sounds belong to
Discord, Inc. and are not covered by these licenses (see [assets/sounds](assets/sounds/README.md)).

The original Serein README, with the full feature list and architecture overview, is kept at
[docs/serein-readme.md](docs/serein-readme.md).
