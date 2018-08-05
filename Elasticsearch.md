shards

replicas

Version:
* Each document have it's own version number count.
* As Update/Delete operations
  * Internal version: version number must match if provided.
  * External version: version number must grater or equal if provided.
* Return status will have the new version number.