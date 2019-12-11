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

### Intel CPU

* C10, PCn, etc.