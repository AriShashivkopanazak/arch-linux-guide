# How To Configure The Network
### Legend:
* '##' = Comments these are pasteable into your terminal, it will not effect anything
## If You Plan To Have a Permanent Wired Connection, Or Installing in VM
    # ip a ## look for your wired connection interface 
    (is the only interface that uses 'e' for 'ethernet' at the beginning 
    of the interface name), ours is enp0s3
    # nano /etc/systemd/network/enp0s3.network ## whatever your wired connection
      [Match]
      name=en*
      [Network]
      DHCP=yes
    # systemctl restart systemd-networkd
    # systemctl enable systemd-networkd
    # nano /etc/resolv.conf
      nameserver 1.1.1.1  ## primary DNS
      nameserver 8.8.8.8  ## optional, this is the backup DNS, you may have as many as you want
    # ping www.github.com
## If You have a wireless adapter
    
