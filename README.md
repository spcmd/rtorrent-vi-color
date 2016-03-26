My modified (patched) version of the [rtorrent-vi-color](https://aur.archlinux.org/packages/rtorrent-vi-color) package from the AUR.

By default a torrent can be deleted accidentally when hitting `Ctrl+d` on a stopped torrent.

With this patch `Ctrl+d` stops the torrent but it doesn't delete it. `Shift+d` (**D**) is used for deleting a torrent from the list.

I renamed the package to `rtorrent-vi-color-spcmd` in the **PKGBUILD** to avoid confusion with the original package.
