
Ubuntu
* prime-select files:
  * /lib/modprobe.d/blacklist-nvidia.conf
  * /lie/modprobe.d/nvidia-kms.conf
  * /etc/gdm3/custom.conf

* RTD3
  * /usr/share/doc/nvidia-driver-460/supported-gpus.json
    * (replace for your driver version)
    * search for runtimepm
  * /lib/modprobe.d/nvidia-runtimepm.conf for parameter as load nv driver.
    * options nvidia "NVreg_DynamicPowerManagement=0x02" # to enable run time pm
  * force gpu-manager to add runtimepm flag
    * touch   /etc/u-d-c-nvidia-runtimepm-override
  * check if parameter in current loading module
    * $ cat /proc/driver/nvidia/params | grep DynamicPowerManagement
    * DynamicPowerManagement: 2 # value 2 means the flag is passed there.

Data Science Pack
  * **https://github.com/NVIDIA/data-science-stack**

Tensorflow and cuda compatiability
  * https://stackoverflow.com/questions/50622525/which-tensorflow-and-cuda-version-combinations-are-compatible
