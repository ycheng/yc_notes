Plugins:
 * use AFTER / BEFORE, etc to decide order.

Relation with oem-config
....
etc.

dell-recovery:
 * kernel boot arg
   * dell-recovery/recovery_type=hdd
   * systemd.debug-shell
   * boot=casper
   * automatic-ubiquity
     * so it will /usr/lib/udisk2/udisks2-inhibit /usr/lib/ubiquity/bin/ubiquity --automatic --only
 * /usr/share/ubiquity/start-ubiquity-dm

oobe:
 * default.target link to oem-config.target (/lib/systemd/system/oem-config.target)
   * so it will run oem-config-firstboot
 * oem-config: oem-config-firstboot