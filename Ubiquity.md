Plugins:
 * use AFTER / BEFORE, etc to decide order.

Relation with oem-config
....
etc.

dell-recovery:
 * /usr/share/ubiquity/start-ubiquity-dm

oobe:
 * default.target link to oem-config.target (/lib/systemd/system/oem-config.target)
   * so it will run oem-config-firstboot
 * oem-config: oem-config-firstboot