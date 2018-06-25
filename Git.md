
Worktree:

* git worktree add -b hotfix ../hotfix master # create a work tree with hotfix branch
* git worktree list # list worktree
* 

Store credential
* Store credential forever
  * git config --global credential.helper store
  * save in ~/.git-credentials
* Cache credential
  * git config --global credential.helper cache # default cache 15 mins
  * git config --global credential.helper 'cache --timeout 3600' # set time out to 1 hour