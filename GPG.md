subkey

* gpg --sign xxx
* gpg --recv-keys KEY_ID # get someone's key from key server


Key Signing
* To sign someone's key (KEY_ID) by my key (MY_KEY_ID)
  * gpg --sign-key KEY_ID # use master key to sign
  * gpg --armor --export KEY_ID | gpg --encrypt -r KEY_ID --armor --output KEY_ID-signedBy-MY_KEY_ID.asc
* Got someone who signed my key
  * gpg -d MY_KEY_ID-signedBy-KEY_ID.asc | gpg --import
  * gpg --send-key MY_KEY_ID # send to key server 