python vmomi

* https://github.com/vmware/pyvmomi
* https://github.com/vmware/pyvmomi-community-samples


Recovery EXSi root password: (mirror of https://vinceto.net/tag/password-recovery/)

1. Boot the server up with a linux disc, such as CentOS 7 in recovery mode
1. Once booted, mount 250MB partition. Usually /dev/sda5. mount /dev/sda5 /mnt
1. cd to /mnt
1. Copy state.tgz to /tmp cp state.tgz /tmp
1. cd to /tmp, then extract state.tgz. cd /tmp; tar -zxvf state.tgz
1. Extract local.tgz. tar -zxvf local.tgz
1. Open the /tmp/etc/shadow file using your favorite text editor. nano /tmp/etc/shadow
1. Under your root (or account with root), remove the shadow password. The resulting row may look like this. root::13358:0:99999:7:::
1. Now repack all the files back in. cd /tmp; tar -zcvf local.tgz etc; tar -zcvf state.tgz local.tgz
1. Copy the state.tgz back into /mnt. cp /tmp/state.tgz /mnt;
1. Now reboot the server. Once ESXi is booted back online, you will be able to log into your root with a blank password.