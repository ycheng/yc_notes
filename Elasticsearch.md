Shards:
* Document in an index can split into shards, so that each shard can run on different node.
* Each Elasticsearch shard is a Lucene index. For LUCENE-5843, max doc per Lucene is Integer.MAX_VALUE - 128.

Replicas:
* 1 means 1 extra copy. So there will be two copy (1 primary and one replica)
* With multiple nodes, provide high-availability.

Version:
* Each document have it's own version number count.
* As Update/Delete operations
  * Internal version: version number must match if provided.
  * External version: version number must grater or equal if provided.
* Return status will have the new version number.