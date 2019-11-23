if you are using UEFI


* What's [swap](https://wiki.archlinux.org/index.php/Swap)?



### Partition the Disks (for UEFI Boards)
    # fdisk /dev/sda ## this refers to your primary disk
Futher Reading:
* How to use [fdisk](https://wiki.archlinux.org/index.php/Fdisk).
* Make partitions:
    * /dev/sda1 = BIOS Boot Partition = 20Mb size
    * /dev/sda2 = Boot Partition = 500Mb size
    * /dev/sda3 = [Swap](https://wiki.archlinux.org/index.php/Swap) Partition is optional = [1000Mb size](https://wiki.archlinux.org/index.php/Swap)
    * /dev/sda4 = Root Partition = rest of the disk
### Format Partitions (for UEFI Boards)
    NOTE: /dev/sda1 should not be formatted, grub will do that for us
    # mkfs.ext2 /dev/sda2 ## Boot Partition gets formatted as a ext2 file system
    # mkswap dev/sda3 ## If you want a swap partition
    # swapon dev/sda3 ## Applies only if you want swap
    # mkfs.ext4 /dev/sda1 ## Your Remaining space, will be used as / partition
Further Reading:
* What's [swap](https://wiki.archlinux.org/index.php/Swap)?
* See also for different file systems: [Btrfs](http://wiki.archlinux.org/index.php/Btrfs).
