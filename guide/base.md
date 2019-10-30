# Installing the Minimal Base System
### Legend: 
* h = Applies solely to if you are installing on your Host machine
* '##' = Comments these are pasteable into your terminal, it will not effect anything

### Partition the Disks
    # fdisk /dev/sda ## this refers to your primary disk, 
    Recommended: make one partition, unless you know what you're doing 
Futher Reading:
* How to use [fdisk](https://wiki.archlinux.org/index.php/Fdisk).
* What's [swap](https://wiki.archlinux.org/index.php/Swap)?
Note: This is the way to prepare disks if you are on a BIOS board, If you are using UEFI, see [here](https://github.com/AriShashivkopanazak/arch-linux-guide/blob/master/guide/uefi.md)
### Format Partitions
    # mkfs.ext4 /dev/sda1
Further Reading:
* See also for different file systems: [Btrfs](http://wiki.archlinux.org/index.php/Btrfs).
### Mount Filesystem
    # mount /dev/sda1 /mnt
### Install Base System
    # pacstrap /mnt base linux grub pacman sed
### Generate Fstab File
    # genfstab -U /mnt >> /mnt/etc/fstab
### Chroot into system
    # arch-chroot /mnt
### Configure Grub
    # grub-install /dev/sda
    # grub-mkconfig -o /boot/grub/grub.cfg
### Where to next?
don't reboot yet! Set your [timezone and locale](https://github.com/AriShashivkopanazak/arch-linux-guide/blob/master/guide/setup.md), install a [gui](https://github.com/AriShashivkopanazak/arch-linux-guide/blob/master/guide/gui.md), and configure the [network](https://github.com/AriShashivkopanazak/arch-linux-guide/blob/master/guide/network.md) while you still connected to the network!
