
* ppa for maas: https://launchpad.net/~maas/+archive/ubuntu/stable
```
sudo add-apt-repository ppa:maas/2.6
sudo add-apt-repository ppa:maas/stable
sudo apt-get update
sudo apt install maas
```

* after deploy, default account is ubuntu. use ssh public key to login.


On Server:
* /var/lib/maas/boot-resources/: images store here, it seems.
* cloud init file like
```
>network:
>    ethernets:
>        enp0s31f6:
>            dhcp4: true
>        enp3s0:
>            dhcp4: false
>            addresses: [192.168.1.1/24]
>    version: 2
```