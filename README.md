# docs
Finally making a place to remember commands / setup stuff I usually forget about.

## flatpak faugus launcher sandbox setup

Due to those *amazing* gacha games, Faugus is sandboxed to just ~/Faugus, umu's steamrt, and installed Proton versions. Proton logs are pinned to ~/Faugus too. (External drives are still visible but whatever)
```
mkdir -p ~/Faugus
flatpak override --user --nofilesystem=home io.github.Faugus.faugus-launcher
flatpak override --user --filesystem=~/Faugus io.github.Faugus.faugus-launcher
flatpak override --user --filesystem=~/.local/share/umu io.github.Faugus.faugus-launcher
flatpak override --user --filesystem=~/.local/share/Steam/compatibilitytools.d io.github.Faugus.faugus-launcher
flatpak override --user --env=PROTON_LOG_DIR=~/Faugus io.github.Faugus.faugus-launcher
```

Also for decent flatpak theming:
```
mkdir -p ~/.themes
cp -rn /usr/share/themes/Breeze /usr/share/themes/Breeze-Dark ~/.themes/
flatpak override --user --filesystem=~/.themes:ro io.github.Faugus.faugus-launcher
flatpak override --user --filesystem=xdg-config/gtk-3.0:ro io.github.Faugus.faugus-launcher
flatpak override --user --filesystem=xdg-config/gtk-4.0:ro io.github.Faugus.faugus-launcher
flatpak override --user --env=GTK_THEME=Breeze:dark io.github.Faugus.faugus-launcher
```