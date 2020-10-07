Box related command:
 * vagrant box list
 * vagrant package --output somerville-vagrant-base.box # create a box for current vagrant (dir)
 * 


Virtualbox + vagrant in focal

 * https://github.com/hashicorp/vagrant/issues/10970
 * vb.customize [ "modifyvm", :id, "--uartmode1", "file", Vagrant::Util::Platform.windows? ? "NUL" : "/dev/null" ]

Virtualbox
* vboxmanage list vms: list existing vm
 * 

Vagrant box dir:
* $HOME/.vagrant.d/boxes




* Simulate dell machine: https://paste.ubuntu.com/p/c6Yn5VCNgX/

```
$ VBoxManage setextradata Ubuntu VBoxInternal/Devices/pcbios/0/Config/DmiOEMVBoxVer "Dell System"
$ VBoxManage setextradata Ubuntu VBoxInternal/Devices/pcbios/0/Config/DmiOEMVBoxRev "1[0962]"
$ VBoxManage getextradata Ubuntu
...
Key: VBoxInternal/Devices/pcbios/0/Config/DmiBIOSReleaseDate, Value: 08/02/2019
Key: VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVendor, Value: Dell Inc.
Key: VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVersion, Value: 1.1.0
Key: VBoxInternal/Devices/pcbios/0/Config/DmiBoardProduct, Value: XPS 13 7390
Key: VBoxInternal/Devices/pcbios/0/Config/DmiBoardVendor, Value: Dell Inc.
Key: VBoxInternal/Devices/pcbios/0/Config/DmiChassisVendor, Value: Dell Inc.
Key: VBoxInternal/Devices/pcbios/0/Config/DmiOEMVBoxRev, Value: 1[0962]
Key: VBoxInternal/Devices/pcbios/0/Config/DmiOEMVBoxVer, Value: Dell System
Key: VBoxInternal/Devices/pcbios/0/Config/DmiSystemFamily, Value: XPS
Key: VBoxInternal/Devices/pcbios/0/Config/DmiSystemProduct, Value: XPS 13 7390
Key: VBoxInternal/Devices/pcbios/0/Config/DmiSystemSKU, Value: string:0962
Key: VBoxInternal/Devices/pcbios/0/Config/DmiSystemVendor, Value: Dell Inc.
```
