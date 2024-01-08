# nwg-clipman

This program is a part of the [nwg-shell](https://nwg-piotr.github.io/nwg-shell) project.

Nwg-clipman is a GTK3-based GUI for Senan Kelly's [cliphist](https://github.com/sentriz/cliphist). It provides access to previously copied items, as well 
as management of the clipboard history from a window opened on gtk-layer-shell. The program is intended for use with
sway, Hyprland and other wlroots-based Wayland compositors.

![image](https://github.com/nwg-piotr/nwg-clipman/assets/20579136/1ce55202-245e-40c2-9d34-b539b5f81261)

## Dependencies

- python >= 3.6;
- python-gobject;
- gtk3;
- gtk-layer-shell;
- wl-clipboard;
- cliphist;
- xdg-utils.

## Installation

The program may be installed by cloning this repository and executing the `install.sh` script (make sure you installed
dependencies first). Then you need to edit your compositor config file, to enable storing clipboard history to cliphist.

Example for sway:

```text
exec wl-paste --type text --watch cliphist store
exec wl-paste --type image --watch cliphist store
```

Example for Hyprland:

```text
exec-once = wl-paste --type text --watch cliphist store
exec-once = wl-paste --type image --watch cliphist store
```

You may omit the second line if you don't want images to be remembered.

Then create a key binding to launch nwg-clipman:

Example for sway:

```text
bindsym Mod1+C exec nwg-clipman
```

Example for Hyprland:

```text
bind = ALT, C, exec, nwg-clipman
```

You may clear the search entry / close the program window with the `Esc` key.

## Options

```text
❯ nwg-clipman -h
usage: nwg-clipman [-h] [-v] [-n] [-w]

options:
  -h, --help     show this help message and exit
  -v, --version  display Version information
  -n, --numbers  hide item Numbers in the list
  -w, --window   run in regular Window, w/o layer shell
```