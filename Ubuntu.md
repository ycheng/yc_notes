
Install Extra Driver:
* $ sudo ubuntu-drivers autoinstall

How to ask kernel not to load certain kernel module - Black list: (to ask kernel not to load nouveau as example)
1. module_blacklist=nouveau: add in kernel boot parameter
2. echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf
3. echo nouveau off > /etc/modprobe.d/balcklist-nouveau-alias-off.conf # this will load module "off" for command "modprobe nouveau", but not such module ("off"), so it will failed.