der / pem
* openssl x509 -inform der -in certificate.cer -out certificate.pem.

Pre-generated mok for dkms and test kernel:
* oem-fix-misc-cnl-sbtestkey_fish1.tar.gz, will install below key to /var/lib/shim-signed
* test_kernel/TestKer.pem
* test_kernel/TestKer.priv
* test_kernel/TestKer.der
* mok/MOK.priv
* mok/MOK.der
* mok/MOK.pem
For the test kernel, if you want it to be used in stage 1, use TestKer.priv and TestKer.pem to sign it.

To Sign test kernel:
* sbsign --key /var/lib/shim-signed/test_kernel/TestKer.priv --cert /var/lib/shim-signed/test_kernel/MOK.pem --output vmlinuz-5.8.13-050813-generic.signed vmlinuz-5.8.13-050813-generic

Check if a key has been enrolled
* mokutil --test-key /var/lib/shim-signed/mok/MOK.der # mok for dkms
* mokutil --test-key /var/lib/shim-signed/test_kernel/TestKer.der # mok for test kernel

To Enroll a key:
* mokutil --import MOK.der
* Will prompt for password
* Enter the password during reboot to enroll the key.

To check if kernel is signed:
* check against canonical certificate
* sbverify --cert /usr/share/grub/canonical-uefi-ca.crt vmlinuz-5.6.0-1028-oem
* Signature verification OK
-------------
* check against mok
* sbverify --cert /var/lib/shim-signed/test_kernel/MOK.pem vmlinuz-5.6.0-1028-oem
* Signature verification OK

EFI Variable:
mok for dkms ?
* EFIVAR=/sys/firmware/efi/efivars/MokKeyEnroll-e22021f7-3a03-4aea-8b4c-65881a2b8881
* EFIVAR=/sys/firmware/efi/efivars/MokKeyTestKer-161a47b3-c116-4942-ae30-cde31ecae242
