configuring the locales
### Set locale
    # nano /etc/locale.gen
    <from there, uncomment your locale, e.g removing '#' from #en_US.UTF-8 will uncomment>
    <save file by using ctrl+x, y, enter>
    # locale-gen
    # echo LANG=<The language you use, e.g en_US.UTF-8 > /etc/locale.conf
    # export LANG=<The language you use, e.g en_US.UTF-8 >
### Set Timezone
    # ln -sf /usr/share/zoneinfo/America/Los_Angeles /etc/localtime
    # hwclock --systohc --utc
### Name System
    # echo <name> > /etc/hostname
    # echo <name> > /etc/hosts
