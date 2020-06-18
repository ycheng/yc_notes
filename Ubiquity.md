Plugins:
 * use AFTER / BEFORE, etc to decide order.

Relation with oem-config
....
etc.

dell-recovery:
 * kernel boot arg
   * dell-recovery/recovery_type=hdd
   * systemd.debug-shell
   * boot=casper (your system and your bootloader on different partitions, set the "boot" argument)
   * automatic-ubiquity
     * so it will /usr/lib/udisk2/udisks2-inhibit /usr/lib/ubiquity/bin/ubiquity --automatic --only
 * /usr/share/ubiquity/start-ubiquity-dm
 * /usr/share/ubiquity/dell-bootstrap
   * dh_input dell-recovery/recovery_type || true
 * ubiquity --pass-output /usr/share/ubiquity/install.py
   * pytho3 /usr/share/ubiquity/install.py
   * balala
 * ubiquity --pass-output /usr/share/ubiquity/plugininstall.py

oobe:
 * default.target link to oem-config.target (/lib/systemd/system/oem-config.target)
   * so it will run oem-config-firstboot
 * oem-config: oem-config-firstboot