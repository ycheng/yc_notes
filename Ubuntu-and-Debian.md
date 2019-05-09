### hot key
* input, acpi event (acpi_listen), wmi
* showkey

### socket
* netstat
* lsof
* ss
* ref: https://unix.stackexchange.com/questions/16300/whos-got-the-other-end-of-this-unix-socketpair

### backlight
* /sys/class/backlight/

### lshw
* lshw: can show hw information. Ex: how many memory slot, and each memory module on each slot.

### msr-tools
* MSRs are Machine Specific Registers that are used to set values for hardware to use, or to pass values between the BIOS and kernel.

### busy kworker
* sudo apt-get install linux-tools-common linux-tools-3.11.0-15-generic # install perf
* sudo perf record -g -a sleep 10 # get log
* sudo perf report # check log
* source: https://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu

### nvlink
* nvidia-smi nvlink -c # 
* simpleP2P # CUDA, NVLINK Peer-To-Peer
* p2pBandwidthLatencyTest # CUDA, NVLINK Peer-To-Peer

### smbios
* $ sudo apt install -y smbios-utils
* $ sudo smbios-token-ctl -v --is-bool  --token-id=0x034f
* $ sudo smbios-token-ctl -v --activate --token-id=0x034f

### debconf
* echo get debconf/frontend | debconf-communicate

### dd
* dd if=XXX.iso of=/dev/sdb conv=fsync status=progress

### secure boot
* mokutil --revoke-import # revoke import
* mokutil --test-key /var/lib/shim-signed/mok/MOK.der
* update-secureboot-policy --new-key # create mok
* printf "123\n123\n" | mokutil --import /var/lib/shim-signed/mok/MOK.der # use 123 as enroll key password
* # install dkms # will enroll key
* mokutil --revoke-import # to cancel enroll mok.

### deb verion retrival
* $ rmadison pkg # in pkg devscripts

### snap
* $ sudo snap connect modem-manager:mmcli modem-manager:service # to have modem-manager snap work.

### tlpui
* https://github.com/d4nj1/TLPUI

### fwupd / fwupdate / gcab
* fwupdmgr install file.cab
* sudo fwupdate -l # to find the guid
* sudo fwupdate -a guid firmware.bin
* reboot after that.
* gcab -x firmware.cab # get firmware.bin from cab file.

### 18.04: change hostname
* https://linuxconfig.org/how-to-change-hostname-on-ubuntu-18-04-bionic-beaver-linux
* $ sudo hostnamectl set-hostname linuxconfig
* set "preserve_hostname: true" for /etc/cloud/cloud.cfg
* modify /etc/hosts, /etc/postfix/main.cf.

### create bootable usb stick in windows
* https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0
* suggest https://rufus.ie/

### debug grub
* add "set debug=all" to the first line of /boot/grub/grub.cfg
* un-comment GRUB_TERMINAL=console from /etc/default/grub
* $ sudo update-grub
* Ref: https://fourdollars.blogspot.com/2013/07/grub2.html

### are you run in giga ethernet in linux?
* $ sudo mii-tool eth0 [-v]
* $ ethtool eth0

### initrd.lx
* 7z e -so ../initrd.lz | cpio -id

### debug s3
* /sys/kernel/debug/wakeup_sources
* "tlp bat" or "powertop --auto-tune". using new kernel.

### ubuntu xorg (gpu-manager)
* xorg.conf any more. We simply create configuration files in /usr/share/X11/xorg.conf.d/
* Ref: https://bugs.launchpad.net/bugs/1667198

### partition label
* FAT32: fatlabel
* ext2/3/4: e2label

### efi shell
* partition type id: ef / EFI (FAT-12/16/32)

### emergency mode
* in kernel boot parameter, add "emergency"
* ref: https://linuxconfig.org/how-to-boot-ubuntu-18-04-into-emergency-and-rescue-mode

### disable suspend for pulseaudio
* comment out "load-module module-suspend-on-idle" from ~/.config/pulse/default.pa or /etc/pulse/default.pa
* Ref: https://askubuntu.com/questions/218444/sound-output-starts-delayed

### pinentry
* tool to ask / cache password, for use case like gpg.
* sudo update-alternatives --config pinentry


### pulseaudio debug
* /etc/pulse/client.conf
  * extra-arguments = -vvvv --log-target=file:/tmp/pa-log.txt
  * reboot


### Ubuntu apt key:
* sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 00000000

### Dell WMI
* echo "module dell_wmi +p" | sudo tee /sys/kernel/debug/dynamic_debug/control

### S3 stress test
* sudo add-apt-repository ppa:firmware-testing-team/ppa-fwts-stable
* sudo apt install fwts
* fwts s3 --s3-sleep-delay=30 --s3-multiple=30 --s3-max-delay=30 --s3-min-delay=30
* "fwts method --dumpfile=acpi.log" ?
* sudo fwts uefirttime # fwts UEFI miscellaneous test

### partition label
* sudo e2label partition label

### fstab
* blkid: to get UUID for partition.
* blkid -p /dev/sda1: to get PARTUUID

### Install Extra Driver:
```
$ sudo ubuntu-drivers autoinstall
```

## Kernel

### S3 / S2IDLE
* /sys/power/mem_sleep: s2idle / deep

### Black list kernel module

How to ask kernel not to load certain kernel module - Black list: (to ask kernel not to load nouveau as example)
1. module_blacklist=nouveau: add in kernel boot parameter
2. echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf
3. echo nouveau off > /etc/modprobe.d/balcklist-nouveau-alias-off.conf # this will load module "off" for command "modprobe nouveau", but not such module ("off"), so it will failed.

### Update initrd
```
$ sudo update-initramfs -u
```

### My Convention

Now it's 18.04

* Gnome Terminal: Ctrl-Shift-C / Ctrl-Shift-V to copy/paste is annonying. I change it to Alt-c / Alt-v
  * How: Gnome Terminal Menu -> Edit -> Preference -> Key -> Change it !

For Chinese use:
* use shift to switch between English / Chinese is not good for me. I hist Shift-Space from time to time
  * I change back to Ctrl-Space to switch Pure English vs Chinese mode.
  * 如何做: 設定程式 => 裝置 => 鍵盤 => (最下面) 輸入 -> 切換到下一個輸入來源 => 設定按鍵.
  * How: Settings => Device => Keyboard => (Bottom) Input -> Switch to next Input Source => Set the key.

### Ubuntu Machine
* http://shop.ekimia.fr/en/: Franch Company that sell Ubuntu Laptop.


### System Driver:
* "lspci -k": list pci device with driver it uses.

###　Booting:
* /etc/modprobe.d/blacklist.conf
* /etc/defaults/grub, modify GRUB_CMDLINE_LINUX_DEFAULT, "sudo update-grub"

### Kernel Parameters:
* acpi_osi="Linux-Dell-Video"
  * result: in bios, _OSI("Linux-Dell-Video") == TRUE
* pcie_aspm=off
  * turn off ASPM
* pcie_aspm.policy=powersupersave
  * max ASPM power saving
* noacpi
  * boot without ACPI


### Debian
* sudo apt-get install command-not-found / sudo update-command-not-found / relogin
*

* ifconfig, netstat will be remove, replaced by iproute2. ref: https://insights.ubuntu.com/2017/07/07/if-youre-still-using-ifconfig-youre-living-in-the-past

* NetPlan: it have two renderers:  NetworkManager and networkd. https://websiteforstudents.com/configure-static-ip-addresses-on-ubuntu-18-04-beta/

### Bionic:

* https://launchpad.net/ubuntu/+source/thunderbolt-tools/0.9.2-1: for server.
* https://launchpad.net/ubuntu/+source/bolt: for Desktop

### Ubuntu - Kernel:
* Unstable Kernel: https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable
* oem kernel: https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/ppa/+packages
* oem kernel: https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/ppa
* oem kernel: https://launchpad.net/ubuntu/+source/linux-meta-oem

### Ubuntu - Security:
* https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/
* https://wiki.ubuntu.com/SecurityTeam/
* https://code.launchpad.net/~ubuntu-security/ubuntu-cve-tracker