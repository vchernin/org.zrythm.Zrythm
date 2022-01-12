Build:

note you need `org.gnome.Platform//master` and `org.gnome.Platform//master` for now.

`flatpak-builder build-dir --user --install org.zrythm.Zrythm.json --force-clean --ccache`

libs I need to link

/app/lib/libfftw3f.so.3.6.10
/app/lib/libfftw3f_threads.so.3.6.10

probably





                    "LDFLAGS": "-L/app/lib -Wl,-z,relro,-z,now -Wl,--as-needed /app/lib/libfftw3f_threads.so /app/lib/libfftw3_threads.so -Wl,-rpath -Wl,/app/lib",
