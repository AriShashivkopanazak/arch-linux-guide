# How To Configure The Network
## If You Plan To Have a Permanent Wired Connection, Or Installing in VM

### add these packages to your pacstrap or install them via pacman -S
    # pacman -S dhcpcd nano
    dhcpcd = assigns an ip address automatically (recommended)
    nano = text editor, you can use vim if you want (required)
    # exit
    # poweroff
    
### When you successfully installed Arch, boot up and excecute these commands
    # ip a
    look for your wired connection interface (is the only interface that uses 'e' for 'ethernet' at the beginning of the interface name), ours is enp0s3
    # nano /etc/systemd/network/enp0s3.network
      [Match]
      name=en*
      [Network]
      DHCP=yes
    # systemctl restart systemd-networkd
    # systemctl enable systemd-networkd
    # nano /etc/resolv.conf
      nameserver 1.1.1.1  ## primary DNS
      nameserver 8.8.8.8  ## optional, this is the backup DNS, you may have as many as you want
    # dhcpcd enp0s3
    # ping www.github.com
    
## If You are using a wireless adapter

### Add these packages to your pacstrap or install them via pacman -S
    # pacman -S wpa_supplicant dhcpcd iw dialog netctl
    wpa_supplicant = used to connect to WPA/WPA2 connections (required)
    dhcpcd = assigns an ip address automatically (recommended)
    iw = used to connect to WEP connection (optional)
    dialog = needed for "wifi-menu" (optional)
    netctl = needed for "wifi-menu" (optional)
    # exit
    # poweroff

### When you successfully installed Arch, boot up and excecute these commands

### Easy Way: Excecute "wifi-menu" to get wifi
    # wifi-menu
    # ping www.google.com
    
