- Bash by example: http://www.gentoo.org/doc/en/articles/bash-by-example-p3.xml?style=printabl
- #gentoo-dev-help

- http://wiki.ubuntuusers.de/Logical_Volume_Manager?redirect=no
- https://wiki.gentoo.org/wiki/Dwm
- http://wiki.gentoo.org/wiki/World
- http://wiki.gentoo.org/wiki/Portage_TMPDIR_on_tmpfs

- make.conf https://wiki.gentoo.org/wiki//etc/portage/make.conf
- example make.conf: http://dev.gentoo.org/~tester/emul/make.conf

- write use flags and per package basis: https://wiki.gentoo.org/wiki//etc/portage/package.use
- all use flags: http://www.gentoo.org/dyn/use-index.xml

- read man emerge and man ebuild
- https://wiki.sabayon.org/?title=En:HOWTO:_The_Complete_Portage_Guide

- for the macbook: http://wiki.gentoo.org/wiki/Apple_Macbook_Pro_Retina

- look at openbox wiki for xinitrc. --exit-with-session? https://wiki.gentoo.org/wiki/Openbox/HOWTO

Info mit welchen flags packet installiert wurde:
 emerge -Opv vim
info was ein flag tut:
 equery u mpv

- setxkbmap de

- flaggie

- schauen wie paket kompiliert wurde:
emerge -vp pkg
oder eix
oder emerge --info pkg

- list all installed packages: http://how-to.wikia.com/wiki/How_to_find_all_packages_emerged(installed)_on_a_Gentoo_Linux_system

- Kompilier Optimierung: http://www.gentoo.de/doc/de/gcc-optimization.xml

# power manager
xfce4-power-manager
also gnome-power-manager exists
http://vincent.bernat.im/en/blog/2011-gnome-power-manager.html

# how to participate in gentoo
http://blogs.gentoo.org/news/2014/03/31/gentoo-monthly-newsletter-march-2014/

# disk
pmount, udev, thunar-volman
find out uuids and then fstab/mount http://liquidat.wordpress.com/2007/10/15/short-tip-get-uuid-of-hard-disks/
https://wiki.archlinux.org/index.php/USB_Storage_Devices

# good overall read for minimal DE
https://wiki.archlinux.org/index.php/openbox
https://wiki.archlinux.org/index.php/desktop_environment#Custom_environments

# displays/monitors
xrandr
arandr
lxrandr

brightness control i3?

# volume control
alsamixer
volumeicon

#keyring, passowords, authentication
https://wiki.archlinux.org/index.php/GNOME_Keyring

#network
http://wiki.gentoo.org/wiki/NetworkManager
emerge nm-applet
or just dhcpcd
rc-update add dhcpcd default

# installation und updates
install:
- emerge -avn prog1 prog2 prog3
update:
- emerge -aDNuv world
- emerge --depclean
- revdep-rebuild
configs:
- dispatch-conf

# source
look for it in /usr/portage/distfiles

you can even have portage unpack it an apply the
patches with `ebuild $(equery w PACAKGENAME) prepare`, then look
in /var/tmp/portage/
then you make a local portage overlay, copy the
ebuild into it, and modify that.
https://wiki.gentoo.org/wiki/Overlay/Local_overlay
also check user_patch epatch_user

##debug in gentoo
http://matija.suklje.name/lazy-mans-guide-to-debugging-in-gentoo

getting "install glibc with debuginfo" in valgrind
the quick one-time fix is `FEATURES=splitdebug emerge -1 sys-libs/glibc`

To make it permanent (after future glibc upgrades/rebuilds) you can either enable FEATURES=splitdebug globally in make.conf which takes up more disk space, or use https://wiki.gentoo.org/wiki/etc/portage/env functionality.

#localisation
http://www.gentoo.org/doc/de/guide-localization.xml

XDefaults
https://wiki.archlinux.de/title/Xdefaults#Other_Resources

# Fonts #
http://kev009.com/wp/2009/12/getting-beautiful-fonts-in-gentoo-linux/
http://forums.gentoo.org/viewtopic-t-985178-highlight-chrome+fonts.html

Inconsolata
DejaVu Sans Mono Book

#GTK Themes
Greybird

## applications ##

# Backup #
[Conduit](http://wiki.ubuntuusers.de/Conduit)
grsync
synkron
unison

# duplicate files/cleanup #
fslint

# X11 Cursors #
gentoo speichert xcursors in /usr/share/cursors/xorg-x11  lxappearance in /usr/share/icons
ln -s /usr/share/cursors/xorg-x11/* /usr/share/icons/
