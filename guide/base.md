# Installing the Base System
### Legend:
* v = Applies solely to VM users 
* h = Applies solely to if you are installing on your Host machine
* '##' = Comments these are pasteable into your terminal, it will not effect anything

### Partition the Disks
    # fdisk /dev/sda ## this refers to your primary disk
Futher Reading:
* How to use [fdisk](https://wiki.archlinux.org/index.php/Fdisk).
* Make partitions:
    * /dev/sda1 = BIOS Boot Partition = 20Mb size
    * /dev/sda2 = Boot Partition = 500Mb size
    * /dev/sda3 = [Swap](https://wiki.archlinux.org/index.php/Swap) Partition is optional = [1000Mb size](https://wiki.archlinux.org/index.php/Swap)
    * /dev/sda4 = Root Partition = rest of the disk
### Format Partitions
    NOTE: /dev/sda1 should not be formatted, grub will do that for us
    # mkfs.ext2 /dev/sda2 ## Boot Partition gets formatted as a ext2 file system
    # mkswap dev/sda3 ## If you want a swap partition
    # swapon dev/sda3 ## Applies only if you want swap
    # mkfs.ext4 /dev/sda1 ## Your Remaining space, will be used as / partition
Further Reading:
* What's [swap](https://wiki.archlinux.org/index.php/Swap)?
* See also for different file systems: [Btrfs](http://wiki.archlinux.org/index.php/Btrfs).
### Mount Filesystem
    # mount /dev/sda1 /mnt
### Install Base System
    # pacstrap /mnt base base-devel
### Chroot Into /mnt
    # arch-chroot /mnt linux ## this is the minimal requirements, however, you can use "base base-devel" for even more tools
### Generate Fstab File
    # genfstab -U /mnt >> /mnt/etc/fstab
### Chroot into system
    # arch-chroot /mnt
### Set Timezone
    # ln -sf /usr/share/zoneinfo/America/Los_Angeles /etc/localtime
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
    # grub-install /dev/sda
    # grub-mkconfig -o /boot/grub/grub.cfg
### Where to next?
don't reboot yet!  install a [gui](https://github.com/AriShashivkopanazak/arch-linux-guide/blob/master/guide/gui.md) and configure the [network](https://github.com/AriShashivkopanazak/arch-linux-guide/blob/master/guide/network.md) while you still have a wired connection!
