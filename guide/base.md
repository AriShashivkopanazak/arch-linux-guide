# Installing the Base System
### Legend:
* v = Applies solely to VM users 
* h = Applies solely to if you are installing on your Host machine
* (o) = optional step
* '<CONTENT>' = extra notes

### Partition the Disks
    # fdisk /dev/sda
How to use [fdisk](https://wiki.archlinux.org/index.php/Fdisk)
### Format all non-swap Partitions as ext4
    # mkfs.ext4 /dev/sda1
    (o) # mkswap dev/sda2
    (o) # swapon dev/sda2
See also for different file systems: [Btrfs](http://wiki.archlinux.org/index.php/Btrfs)
### Mount Filesystem
    # mount /dev/sda1 /mnt
### Install Base System
    # pacstrap /mnt base base-devel
### Generate Fstab File
    # genfstab -U /mnt >> /mnt/etc/fstab
### Chroot into system
    # arch-chroot /mnt
### Set Timezone
    # ln -sf /usr/share/zoneinfo/<Region you live in, e.g America>/<City you reside in, e.g Los_Angeles> /etc/localtime
    # hwclock --systohc --utc
### Set locale
    # nano /etc/locale.gen
    <from there, uncomment your locale, e.g removing ampersand from #en_US.UTF-8 will uncomment>
    <save file by using ctrl+x, y, enter>
    # locale-gen
    # echo LANG=<The language you use, e.g en_US.UTF-8 > /etc/locale.conf
    # export LANG=<The language you use, e.g en_US.UTF-8 >
### Name System
    # echo <name> > /etc/hostname
    # echo <name> > /etc/hosts
### Install Grub
    # pacman -S grub
    # grub-install /dev/sdX
    # grub-mkconfig -o /boot/grub/grub.cfg
### Where to next?
don't reboot yet!  install a [gui](https://github.com/AriShashivkopanazak/arch-linux-guide/blob/master/guide/gui.md) and configure the [network](https://github.com/AriShashivkopanazak/arch-linux-guide/blob/master/guide/network.md) while you still have a wired connection!
