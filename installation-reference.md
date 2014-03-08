# Gentoo Installation Reference

Use SystemRescueCD

## Preparation

### Partitioning

- *fdisk*
...for *M*aster *P*artition *T*ables with MBR. Use *cfdisk* for the ncurses interface.
- *gdisk*
...for drives with GUID-GPT partition tables. Use *cgdisk* for the graphical interface.

TODO: LVM/CRYPT?

We will asume you have the following partition scheme:
```
/dev/sda1 boot
/dev/sda2 swap
/dev/sda5 /
```

### Creating the filesystems
Creating swap and formatting /boot as ext2 and / as ext3.
```
mkswap /dev/sda2
swapon /dev/sda2

mke2fs -L /boot /dev/sda1
mke2fs -j -L / /dev/sda5
```

### Mounting into the live live environment
```
mkdir -p /mnt/gentoo
mount /dev/sda5 /mnt/gentoo

mkdir /mnt/gentoo/boot
mount /dev/sda1 /mnt/gentoo/boot
```
Now switch into the /mnt/gentoo directory.

### Getting the Stage archive and portage tree

Navigate to http://www.gentoo.org/main/en/mirrors.xml

Choose a mirror near you and go to ```releases/{arch}/current-stage3/stage3-amd64-{creationdate}.tar.bz2```. You can use the browser *links* for that.

Also download ``snapshots/portage-latest.tar.bz2```

Unpack via
```
tar xjpf stage3-whatever.tar.bz2
tar xvjf gentoo-portage-latest.tar.bz2 -C /mnt/gentoo/usr
```

### Change into chroot environment

- first copy resolv.conf so we have a network connection.
```
cp -L /etc/resolv.conf /mnt/gento/etc/resolv.conf
```
- mount proc, sys and dev
```
mount -t proc none /mnt/gentoo/proc
mount -o bin /dev /mnt/gentoo/dev
mount -o bin /sys /mnt/gentoo/sys
```
- choose a mirrror for TODO and set SYNC
```
mirrorselect -i -o >> /mnt/gentoo/etc/make.conf
vim /mnt/gentoo/etc/make.conf
```
.../mnt/gentoo/etc/make.conf:
```
#for europe:
SYNC="rsync://sync.europe.gentoo.org/gentoo-portage"
#for germany:
SYNC="rsync://sync.de.gentoo.org/gentoo-portage"
```
- chroot and finishing steps
```
chroot /mnt/gentoo /bin/bash
env-update
source /etc/profile

#now get the newest portage tree
emerge --sync
#TODO:
cp /usr/share/zoneinfo/CET /etc/localtime
```

### Kernel
```
emerge gentoo-sources
emerge genkernel
genkernel --menuconfig --splash all
```
## Bootloader
```
emerge grub
grub2-install /dev/sda
grub2-mkeconfig >> /etc/boot/grub/grub.cfg
```
