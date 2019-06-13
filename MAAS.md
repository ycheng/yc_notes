
* after deploy, default account is ubuntu. use ssh public key to login.


On Server:
* /var/lib/maas/boot-resources/: images store here, it seems.
* cloud init file like

>network:
>    ethernets:
>        enp0s31f6:
>            dhcp4: true
>        enp3s0:
>            dhcp4: false
>            addresses: [192.168.1.1/24]
>    version: 2
