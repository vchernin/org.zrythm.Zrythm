# Zrythm Flatpak

Flatpak build of [Zrythm](https://www.zrythm.org), a highly automated and intuitive digital audio workstation.

## Plugins

This package Flatpak builds of LV2  LV2, LADSPA, DSSI and Linux VST/VST3 plugins. Plugins not installed as Flatpak cannot be used.

## JACK Support

You need to install `pipewire-jack-audio-connection-kit` (included in Fedora) or `pipewire-jack` (Arch) which replaces JACK with the PipeWire implementation of JACK. Using normal JACK (i.e no PipeWire) is not supported.

## Memory Locking
At runtime you might be warned about memory locking. Memory locking priviliges are useful for reliable, dropout-free operation. This is not specific to Flatpak.

You can follow [the guide listed in the Zrythm docs](https://manual.zrythm.org/en/getting-started/system-requirements.html#gnu-linux).

Todo
- test basic functionality, maybe try https://manual.zrythm.org/en/getting-started/running-zrythm.html#first-run-wizard, and audio plugins
- decide on x-checker-data
make nightly? make follow tags? (requires custom regex).

Maintainer notes:

Build:

1. `git clone https://github.com/vchernin/org.zrythm.Zrythm`

2.  `flatpak install --user org.gnome.Platform//41 org.gnome.Sdk//41 -y` (if not already present)

3. `flatpak-builder build-dir --user --install org.zrythm.Zrythm.json --force-clean --ccache`
OR  
3. `flatpak-builder --repo=zrythm --force-clean --user build-dir org.zrythm.Zrythm.json`  
`flatpak remote-add --user zrythm zrythm --no-gpg-verify`  
`flatpak install --user zrythm org.zrythm.Zrythm`  

4. `flatpak run org.zrythm.Zrythm`

When building with ccache, sometimes vamp-plugin-sdk complains about the object file, rm .flatpak-builder and build-dir (i.e. reset the cache) to fix it.

When upstream uses native PipeWire API (not PipeWire-JACK) will need:
- ensure settings "manager" permission https://gitlab.freedesktop.org/pipewire/pipewire/-/issues/667#note_787310