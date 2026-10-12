# DroidNative Presets

This repository contains a collection of button layouts, patches and additional data and helpers for making xbps, AppImage or Flatpak packages work better when integrated into android.

## Layout:

```
xbps/ - Presets for xbps packages
appimage/ - Presets for appimage packages
flatpak/ - Presets for flatpak packages
```

All presets are named with a `"source/packagename/"` schema such as for example `"xbps/opera/"`.

## Submitting Presets

If you made a button layout / settings preset for a piece of software, please create a pull request in which you added your preset as a commit in the following format (all sections are optional):

```
packagename/
          - settings.ini
          - layout.xml
          - helpers/
                  - <scripts go here>
          - preinstall.sh
          - postinstall.sh
```

DroidNative pulls helpers into `/etc/DroidNative/helpers/<manager>/<packagename>/`.

### settings.ini

Per-app settings, one section per desktop entry of the package (the
`.desktop` file name without its extension; a package can have several).
Every key is optional; a missing key keeps DroidNative's global setting.

```ini
[org.luanti.luanti]
backend = zink          ; auto, zink, gl4es or llvmpipe
resolution = 75%        ; pixels along the short side (720) or a percentage
dpi = 96                ; UI density
input = touchpad        ; touch, mouse or touchpad
rotation = landscape    ; auto, portrait or landscape
auto-keyboard = false   ; open the on-screen keyboard in text fields
children = all          ; who else gets these settings: all, unlisted or none
layout = layout.xml     ; button layout in this folder
```

`layout.xml` is a button layout as DroidNative exports it (Buttons tab,
Export). `preinstall.sh` and `postinstall.sh` run as the guest user before
and after the package is installed.

## Licence

This repository is free software under the GNU General Public License, version 3 or later.

Scripts added to this repository may ship their own licence but are required to use a free software licence. Any addition made without providing its own licence will automatically fall under the GNU GPL v3.
