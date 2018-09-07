
### fstab
  * blkid: to show uuid for partition.

### Install Extra Driver:

* $ sudo ubuntu-drivers autoinstall

### Black list kernel module

How to ask kernel not to load certain kernel module - Black list: (to ask kernel not to load nouveau as example)
1. module_blacklist=nouveau: add in kernel boot parameter
2. echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf
3. echo nouveau off > /etc/modprobe.d/balcklist-nouveau-alias-off.conf # this will load module "off" for command "modprobe nouveau", but not such module ("off"), so it will failed.


### My Convention

Now it's 18.04

* Gnome Terminal: Ctrl-Shift-C / Ctrl-Shift-V to copy/paste is annonying. I change it to Alt-c / Alt-v
  * How: Gnome Terminal Menu -> Edit -> Preference -> Key -> Change it !

For Chinese use:
* use shift to switch between English / Chinese is not good for me. I hist Shift-Space from time to time
  * I change back to Ctrl-Space to switch Pure English vs Chinese mode.
  * 如何做: 設定程式 => 裝置 => 鍵盤 => (最下面) 輸入 -> 切換到下一個輸入來源 => 設定按鍵.
  * How: Settings => Device => Keyboard => (Bottom) Input -> Switch to next Input Source => Set the key.