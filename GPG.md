subkey

* gpg --sign xxx


sign key
* gpg --sign-key KEY_ID # use master key to sign
* gpg --armor --export KEY_ID | gpg --encrypt -r KEY_ID --armor --output KEY_ID-signedBy-MY_KEY_ID.asc