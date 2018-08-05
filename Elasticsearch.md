shards

replicas

Version:
* Each document have it's own version number count.
* (Update) operation will failed if you provide a version number that's not match current one.
* Return status will have the new version number.