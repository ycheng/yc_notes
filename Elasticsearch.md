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

# Get a document
GET /customer/_doc/1?pretty

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

Shell Command (via curl)
```
curl -H "Content-Type: application/json" -XPOST "localhost:9200/bank/_doc/_bulk?pretty&refresh" --data-binary "@accounts.json"
curl "localhost:9200/_cat/indices?v"
```