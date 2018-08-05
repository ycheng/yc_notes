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