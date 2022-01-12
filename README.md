Note this builds and passes basic smoke runtime tests (as in doesn't immediately crash), but is otherwise completly untested.

Todo
- audio plugins
- look for warnings
- test basic functionality
- clean up manifest if possible.

Build:

1. Clone this 

2.  `flatpak install --user org.kde.Platform//5.15-21.08 org.kde.Sdk//5.15-21.08 -y` (if not already present)

Then

3. `flatpak-builder build-dir --user --install org.zrythm.Zrythm.json --force-clean --ccache`

4. `flatpak run org.zrythm.Zrythm`



Random notes:

Sometimes vamp-plugin-sdk complains about the object file, rm .flatpak-builder and build-dir (i.e. reset the cache) to fix it.