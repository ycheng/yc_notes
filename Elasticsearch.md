Shards:
* Document in an index can split into shards, so that each shard can run on different node.
* Each Elasticsearch shard is a Lucene index. For LUCENE-5843, max doc per Lucene is Integer.MAX_VALUE - 128.
* Can NOT be changed after index created.

Replicas:
* 1 means 1 extra copy. So there will be two copy (1 primary and one replica)
* With multiple nodes, provide high-availability.
* Can be changed after index created.

Version:
* Each document have it's own version number count.
* As Update/Delete operations
  * Internal version: version number must match if provided.
  * External version: version number must grater or equal if provided.
* Return status will have the new version number.

-------

Search
```
GET /customer/_search?q=*&sort=age:asc&pretty

GET /customer/_search
{
  "query": { "match_all": {} },
  "sort": [
    { "age": "asc" }
  ]
}

# which are returned.
GET /customer/_search
{
  "query": { "match_all": {} },
  "from": 10,
  "size": 10,
  "sort": { "age": { "order": "desc" } }
}
```
-------

TODO: https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-termvectors.html

------

```
GET _search
{
  "query": {
    "match_all": {}
  }
}

# list all index
GET /_cat/indices?v

# create index customer
PUT /customer?pretty
GET /_cat/indices?v

#  delete index
DELETE /customer?pretty
GET /_cat/indices?v

# put/replace a document to index with specific id
PUT /customer/_doc/1?pretty
{
  "name": "John Doe 鄭",
  "age": 30
}

# put a document to index and ES will return id
POST /customer/_doc?pretty
{
  "name": "Jane Doe Lee"
}

# failed if it already exists
PUT /customer/_doc/1?op_type=create
or
PUT /customer/_doc/1/_create

# put a document with routing (on shard placement)
POST customer/_doc?routing=kimchy

# Get a document
GET /customer/_doc/1?pretty

# check document exists
HEAD customer/_doc/1

# update a document with partial fields
POST /customer/_doc/1/_update?pretty
{
  "doc": { "age": 31 }
}

# update a document with script
POST /customer/_doc/1/_update?pretty
{
  "script" : "ctx._source.age += 5"
}

# delete a document. result will be either deleted or not_found
DELETE /customer/_doc/1?pretty

# bulk update
POST /customer/_doc/_bulk?pretty
{"index":{"_id":"1"}}
{"name": "John Doe" }
{"index":{"_id":"2"}}
{"name": "Jane Doe" }

# bulk update
POST /customer/_doc/_bulk?pretty
{"update":{"_id":"1"}}
{"doc": { "name": "John Doe becomes Jane Doe" } }
{"delete":{"_id":"2"}}
```

Snapshot
```
GET /_snapshot
PUT /_snapshot/backup
{
  "type": "fs",
  "settings": {
    "location": "/data/directory/path"
  }
}
```

Shell Command (via curl)
```
curl -H "Content-Type: application/json" -XPOST "localhost:9200/bank/_doc/_bulk?pretty&refresh" --data-binary "@accounts.json"
curl "localhost:9200/_cat/indices?v"
```