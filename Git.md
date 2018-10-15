### find information

* git tag --contains commit-hash


### File name in non-ascii (like CJK)

* git config core.quotepath false

### Worktree

* git worktree add -b hotfix ../hotfix master # create a work tree with hotfix branch
* git worktree list # list worktree
* 

### Store credential
Password store in plain text. Use it on your own risk.
* Store credential forever
  * git config --global credential.helper store
  * save in ~/.git-credentials
* Cache credential
  * git config --global credential.helper cache # default cache 15 mins
  * git config --global credential.helper 'cache --timeout 3600' # set time out to 1 hour
* save http/https account:
  * git config credential.https://gitlab.aiacademy.tw.username ycheng.tw@gmail.com
