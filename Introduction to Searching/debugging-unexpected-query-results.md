# Debugging unexpected query results

```
GET /products/_doc/1/_explain
{
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```