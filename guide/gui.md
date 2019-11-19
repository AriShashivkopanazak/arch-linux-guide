# Install a GUI
## If you have a graphics card, install their driver
### AMD
    # pacman -S xf86-video-amdgpu
### Intel
    # pacman -S xf86-video-intel
### Nvidia
    # pacman -S xf86-video-nouveau
## KDE
### Make a New User
    # useradd -m -g users ari
    # passwd ari
### Install KDE
    # pacman -S xorg-xinit xorg sddm plasma konsole plasma-nm kdeplasma-addons plasma-pa
### Enable Login Manager
    # systemctl enable sddm
### Reboot
    # reboot
## Gnome
### Make a New User
    # useradd -m -g users ari
    # passwd ari
### Install KDE
    # pacman -S gnome gdm
### Enable Login Manager
    # systemctl enable gdm
### Reboot
    # reboot
## DWM
### Make a New User (Optional)
    # useradd -m -g users ari
    # passwd ari
### Install Tools
    # pacman -S xorg xorg-xinit git vim base-devel
### Change Directory to user (Optional)
    # cd /home/ari
### Make a Folder Named ".dwm"
    # mkdir .dwm
    # cd .dwm
### clone repos for dwm (window manager), st (terminal), and dmenu (application menu)
    # git clone git://git.suckless.org/dwm
    # git clone git://git.suckless.org/st
    # git clone git://git.suckless.org/dmenu
### Compile Each Repo
    # cd dwm
    # sudo make clean install
    # cd ..
    # cd st
    # sudo make clean install
    # cd ..
    # cd dmenu
    # sudo make clean install
### login as new user
    # exit
### Create ".xinitrc"
    # vim .xinitrc
    Add line "exec dwm" into it, save it, and quit
### initiate "startx" as user
    # startx
## Known fixes to Bugs in X
### Xorg error (1)
    find the pid of systemd init
    # htop
    kill the process
    # kill <PID>
    
