Gui stuff
<br>
  
  
  
  set password for root account
                        passwd
        Make new user
                useradd -m -g users <username>
                passwd <username>
        Install Desktop Environment
                pacman -S xorg-xinit xorg-server
                If KDE
                        sddm plasma konsole plasma-nm kdeplasma-addons plasma-pa
			systemctl enable sddm
                If Gnome:
                        gnome gdm
                If dwm:
                        pacman -S xorg-xinit xorg-server git
                        git clone git://git.suckless.org/dwm
                        git clone git://git.suckless.org/dmenu
                        git clone git://git.suckless.org/st
                        cd dwm
                        vim config.mk
                        sudo make clean install
                        cd dmenu
                        vim config.mk                        
                        sudo make clean install
                        cd st
                        vim config.mk
                        sudo make clean install
        Network
                for permanent wired or virtual machine connections:
                        ip a
                        vim /etc/systemd/network/<wired interface>.network
                                [Match]
                                name=en*
                                [Network]
                                DHCP=yes
                        vim /etc/resolv.conf
                                nameserver 1.1.1.1
                                nameserver 8.8.8.8
                                #or any DNS
                        systemctl restart systemd-networkd
                        systemctl enable systemd-networkd
                for Command line wifi manager
                        pacman -S dialog wpa_supplicant
                        wifi-menu
                for KDE wifi
                        systemctl enable NetworkManager
                make sure it works
                        ping www.google.com
        install graphics drivers
                AMD
                        pacman -S xf86-video-amdgpu
                Intel
                        pacman -S xf86-video-intel
                Nvidia
                        pacman -S xf86-video-nouveau
                recommended or vbox:
                        pacman -S xf86-video-vesa
        Necessary applications
		pacman -S konsole plasma-nm kdeplasma-addons plasma-pa
		        systemctl enable NetworkManager
			systemctl enable sddm
                        exit
                        poweroff
                open konsole and type
                        visudo
                install applications:
                        pacman -S kdenlive libreoffice code atom nautilus firefox
                        kdenlive
                        libreoffice
                        code
                        atom
                        nautilus
                        firefox
                        gparted
                        git
                        gedit
                        jre-openjdk
                        jdk-openjdk
                        
                        
