
Store credential
* Store credential forever
  * git config --global credential.helper store
  * save in ~/.git-credentials
* Cache credential
  * git config --global credential.helper cache # default cache 15 mins
  * git config --global credential.helper 'cache --timeout 3600' # set time out to 1 hour