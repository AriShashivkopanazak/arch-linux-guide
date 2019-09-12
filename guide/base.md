Install Base System
                partition disks
                                fdisk /dev/sdX
                format disks
                        mkfs.ext4 /dev/sdX<any partition that is not swap space>
                        mkswap /dev/sdX<any partition that you want as swap space>
                        swapon /dev/sdX
                mount filesystem
                        mount /dev/sdX<root partition> /mnt
                        optional: mkdir /mnt/<home, or whatever>
                        optional: mount /dev/sdX /mnt/<home, or whatever>
                install base system
                        pacstrap /mnt base base-devel
                generate fstab file
                        genfstab -U /mnt >> /mnt/etc/fstab
                chroot into system
                        arch-chroot /mnt
                set timezone
                        ln -sf /usr/share/zoneinfo/<Region>/<City> /etc/localtime
                        hwclock --systohc --utc
                set locale
                        nano /etc/locale.gen
                        locale-gen
                        echo LANG=en_US.UTF-8 > /etc/locale.conf
                        export LANG=en_US.UTF-8
                name system
                        echo <name> > /etc/hostname
                        echo <name> > /etc/hosts
                install grub
                        pacman -S grub
                        grub-install /dev/sdX
                        grub-mkconfig -o /boot/grub/grub.cfg
