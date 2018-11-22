# Debugging unexpected query results

```
GET /product/_doc/1/_explain
{
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```