
* echo blacklist evbug > /etc/modprobe.d/evbug.conf
* firmware-atheros: to make athros wifi work (ex: ath10k). This is in non-free.


Developer
* local archive
  * apt-ftparchive packages . > Packages
  * source list: deb [trusted=yes] file:///path/repo ./

* in deb/control, variables are defined:
  * DEBIAN_VERSION_UPSTREAM