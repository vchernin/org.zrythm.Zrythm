Note this builds and passes basic smoke runtime tests (as in doesn't immediately crash), but is otherwise completly untested.

Todo
here (in this manifest)
- Give permissions for [Memory Locking](https://manual.zrythm.org/en/getting-started/system-requirements.html#memory-locking) (needed for reliable operation, but maybe not the case with PipeWire).
- audio plugins
- look for warnings
- test basic functionality
- clean up manifest if possible.
- Use guile 3, don't need to cleanup (but flathub build will show donation prompt)
- get icons dark only from https://github.com/KDE/breeze-icons, don't cmake it


upstream:
- send metainfo file
- ensure settings "manager" permission https://gitlab.freedesktop.org/pipewire/pipewire/-/issues/667#note_787310


Build:

1. `git clone https://github.com/vchernin/org.zrythm.Zrythm`

2.  `flatpak install --user org.kde.Platform//5.15-21.08 org.kde.Sdk//5.15-21.08 -y` (if not already present)

3. `flatpak-builder build-dir --user --install org.zrythm.Zrythm.json --force-clean --ccache`
OR
3. `flatpak-builder --repo=zrythm --force-clean --user build-dir org.zrythm.Zrythm.json`
`flatpak remote-add --user zrythm zrythm --no-gpg-verify`
`flatpak install --user zrythm org.zrythm.Zrythm`

4. `flatpak run org.zrythm.Zrythm`


Or

Repo build:

flatpak-builder --repo=zrythm --force-clean --user build-dir org.zrythm.Zrythm.json

Limitations:

JACK Support

You need to install `pipewire-jack-audio-connection-kit` which replaces JACK with the PipeWire implementation of JACK. Using normal JACK is not supported.

Random notes:

Sometimes vamp-plugin-sdk complains about the object file, rm .flatpak-builder and build-dir (i.e. reset the cache) to fix it.