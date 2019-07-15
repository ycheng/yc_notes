### Official link ###
* https://wiki.ubuntu.com/Apport

### Directories and files ###
* /usr/share/apport/symptoms
* /usr/share/apport/package-hooks

### How it hook to os ###
* cat /proc/sys/kernel/core_pattern 
* |/usr/share/apport/apport %p %s %c %d %P
