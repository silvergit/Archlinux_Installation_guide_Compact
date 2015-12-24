# Archlinux Installation guide - Compact
---

Copyright (C)  2015  Alireza Pazhouhesh.
Permission is granted to copy, distribute and/or modify this document under the terms of the GNU Free Documentation License, Version 1.3 or any later version published by the Free Software Foundation.

---
```
Partition table
/dev/sda1 --> /
/dev/sda2 --> /home
/dev/sda3 --> swap

User mode
#         --> root user
$         --> normal user
```
---

`# mkfs.ext4 /dev/sda1`

`# mkfs.ext4 /dev/sda2`

`# mkswap /dev/sda3`

`# swapon /dev/sda3`

`# mount /dev/sda1 /mnt`

`# mkdir /mnt/home`

`# mount /dev/sda2 /mnt/home`

`# pacstrap -i /mnt base base-devel`

`# genfstab -U -p /mnt | sed 's/rw,relatime,data=ordered/defaults,relatime/' >> /mnt/etc/fstab`

`# arch-chroot /mnt`

`# nano /etc/locale.gen`

`# locale-gen`

`# echo LANG=en_US.UTF-8 > /etc/locale.conf`

`# export LANG=en_US.UTF-8`

`# ln -s /usr/share/zoneinfo/Iran /etc/localtime`

`# hwclock --systohc --utc`

`# echo localhost > /etc/hostname`

`# systemctl enable dhcpcd@<interface>.service`

`# pacman -S wireless_tools wpa_supplicant wpa_actiond dialog`

`# passwd`

`# useradd -m -g users -G wheel,audio,video,root,storage,lp -s /bin/bash USER_NAME`

`# passwd USER_NAME`

`# pacman -S grub-bios os-prober`

`# grub-install --target=i386-pc --recheck /dev/sda`

`# cp /usr/share/locale/en\@quot/LC_MESSAGES/grub.mo /boot/grub/locale/en.mo`

`# grub-mkconfig -o /boot/grub/grub.cfg`

`# exit`

`# umount /mnt/home`

`# umount /mnt`

`# reboot`

`# pacman -S alsa-utils alsa-plugins`

`$ alsa-mixer`

`# nano /etc/pacman.conf`
```
[archlinuxfr]
Server = http://repo.archlinux.fr/i686

OR

[archlinuxfr]
Server = http://repo.archlinux.fr/x86_64
```

`# pacman -S xorg-server xorg-xinit xorg-server-utils`

`# pacman -S mesa`

`# pacman -S xf86-video-ati`

`# pacman -S xf86-input-synaptics`

`# pacman -S ttf-dejavu`

`# pacman -S gnome gnome-extra`

`# systemctl enable gdm.service`

`# pacman -S mplayer dvd+rw-tools libdvdread libdvdcss ntfs-3g dosfstools gstreamer0.10-{bad,base,good,ugly}-plugins gstreamer0.10-{base,ffmpeg,good,ugly} flashplugins vlc firefox smplayer pidgin goldendict rhythmbox gimp libreoffice-fresh conky plank wine`