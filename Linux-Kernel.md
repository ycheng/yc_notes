### Disable certain run time pm for certain pci id
 * https://askubuntu.com/questions/185274/how-can-i-disable-usb-autosuspend-for-a-specific-device
 * 
```
# udev rule
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="0624", ATTR{idProduct}=="0013", ATTR{product}=="SC Secure KVM", TEST=="power/control", ATTR{power/control}:="on"
# udevadm info -a --path /sys/bus/usb/devices/N-N
```

### power/control
 * on: preventing the device from being runtime power-managed.
 * auto: allowing the device to be runtime power-managed by its driver.

### Alsa
* add "options snd-hda-codec-hdmi dyndbg" in the /etc/modprobe.d/alsa-base.conf. Reboot and check dmesg.

### OSI String
* _OSI(Linux-Dell-Video) 
* BIOS check OS if certain OSI String is supported.

### Create /dev/ device node
 * use kernel function device_create to create device node in /dev/.

### ZFS
 * Deletes in ZFS are expensive. Even more so if you have deduplication enabled on the filesystem (since dereferencing deduped files is expensive). Snapshots could complicate matters too.  https://serverfault.com/questions/801074/delete-10m-files-from-zfs-effectively

### Suspend
 * https://www.kernel.org/doc/Documentation/power/states.txt
 * go to suspend: # echo mem > /sys/power/state
 * config s2idle or s3:
 * "# echo s2idle > /sys/power/mem_sleep # suspend to idle"
 * "# echo deep > /sys/power/mem_sleep # s3"

### Cgroup

### ACPI

* brightness adjustment hot-key: ACPI event ?
* acpidbg -b "notify _SB.PWRB 0x80" # simulate power key

### Intel CPU

* C10, PCn, etc.
