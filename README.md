# Dominique's Hyprland Starting Guide

## Index

1. Install Hyprland
2. Setup application launcher
3. Setup waybar
4. Setup multiple monitors
5. Setup wallpaper



## 1. Install Hyprland

Installing Hyprland is quite easy, and it's best to check the specific instructions
for your Linux distribution.

In case of Arch Linux use the following command, it'll install additional tools
we'll be using as well.

```sh
$ sudo pacman -S hyprland waybar hyprpaper wofi
```


## 2. Setup application launcher

As application launcher we'll be using `wofi`.

It is also the default in the default Hyprland configuration. But depending on
your preferences you might prefer the terminal command over their menu naming,
E.g. `firefox` vs `Firefox Web Browser`.

To change this edit the Hyprland configuration file `~/.config/hypr/hyprland.conf`,
and change the line `$menu = wofi --show run` to `$menu = wofi --show drun`.

Now you can call your application launcher using `META + R`.


## 3. Setup waybar

If you're familiar with the i3 desktop environment you might've noticed we're
missing a toolbar with system information, and background application icons.

To fix this we'll be using waybar.

We have it already installed by now, so all we need to do is to modify our
Hyprland config to start waybar on startup.

Add the following line to the end of `~/.config/hypr/hyprland.conf`.
```
exec-once=waybar
```

Now copy the configuration files from `/etc/xdg/waybar/` to `~/.config/waybar/`
Now edit the file `./config/waybar/config`, and replace all references to 
`sway/workspaces` with `hyprland/workspaces`, and `sway/window` with
`hyprland/window`

More information can be found here. [Hyprland Wiki](https://wiki.hyprland.org/Useful-Utilities/Status-Bars/)


## 4. Setup multiple monitors

Using multiple monitors in Hyprland is easy.

First you need to know the identifies of your displays. You can get these
using the following command:

```sh
$ hyprctl monitors all
```

In my case it returns 2 displays. 
1. DP-2 running at 2560x1440@59.95100
2. DP-3 running at 3440x1440@99.98200

Now edit the Hyprland config file `~/.config/hypr/hyprland.conf`, adjust the
following lines, and add them

```
monitor=DP-3, 3440x1440@99.98200, 0x0, 1
monitor=DP-2, 2560x1440, 3440x0, 1
```

Parameters:
1. Monitor identifier
2. Monitor resolution @ refresh rate
3. Monitor position
4. Monitor scale

More information can be found here. [Hyprland Wiki](https://wiki.hyprland.org/Configuring/Monitors/)


## 5. Setup wallpaper

As a wallpaper manager we'll be using `hyprpaper`.

First we'll need to configure it, for this create a new configuration file at
`~/.config/hypr/hyprpaper.conf`, and fill it with the following settings.

```
preload=/home/username/Pictures/wallpaper.png
wallpaper=/home/username/Picures/wallpaper.png
splash = true
```

- preload

Preload will load all defined images into ram on startup.
Be careful to not load too many pictures here.

- wallpaper

The wallpaper which will be shown.

- splash

If splash text shall be rendered over the wallpaper


To learn more about the different options, like different wallpapers per
monitor, or a slideshow of different wallpapers, check out the 
[Hyprpaper documentation on their GitHub](https://github.com/hyprwm/hyprpaper)


## Done

By now we have a Hyprland setup ready to go!

Thanks for using this guide. If there's anything outdated, or wrong, feel free
to open up a Pull Request or Issue. I'll happily mention your contributions here
as well.


Made with love <3 - Dear Dominique

