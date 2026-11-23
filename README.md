# VCVRack Holon.ist

> ## [→ w0ts.github.io/VCVRack-Holon.ist](https://w0ts.github.io/VCVRack-Holon.ist/)
> **What the seven Holonic Systems modules do, how to install them, Holonic Source's OSC format and the demo patches: on the site.**
> This README is for developers.

The Holonic Systems plugin for VCV Rack 2 (slug `HolonicSystems-Free`), in the
[VCV Library](https://library.vcvrack.com/HolonicSystems-Free). CC0 ([LICENSE.txt](LICENSE.txt)).

## Layout

| Path | What |
|---|---|
| `plugin.json` | The manifest: slug, version, modules, URLs |
| `src/` | The modules (`HolonicSystems*.cpp`), the OSC receiver (`OSCServer`, `tinyosc`) and the mDNS announcer (`MdnsServer`) |
| `res/` | The panels (SVG) |
| `demos/` | Demo patches, shipped with the plugin |
| `Holonic_Source_windows.bat`, `Holonic_Source_linux.sh` | Announce Holonic Source over Bonjour / Avahi on Windows and Linux (macOS does it from the module) |
| `site/` | The user site, deployed by `.github/workflows/pages.yml` |

## Build

With the [Rack 2 SDK](https://vcvrack.com/manual/PluginDevelopmentTutorial):

```
make RACK_DIR=<path to Rack-SDK>
make RACK_DIR=<path to Rack-SDK> install    # into your Rack user folder
```

On Windows the Makefile adds `-DARCH_WIN` itself: the OSC and mDNS sources do not include Rack's `arch.hpp`.

## Release

Bump `version` in `plugin.json`. The VCV Library builds a release from a commit it pins; nothing is requested from it
for now.
