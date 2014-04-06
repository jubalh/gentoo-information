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

- emerge -Opv vim

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
