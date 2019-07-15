### Official link ###
* https://wiki.ubuntu.com/Apport

### How it hook to os ###
* cat /proc/sys/kernel/core_pattern 
* |/usr/share/apport/apport %p %s %c %d %P
