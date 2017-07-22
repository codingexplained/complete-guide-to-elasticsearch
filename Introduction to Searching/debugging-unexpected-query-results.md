# Debugging unexpected query results

```
GET /product/default/1/_explain
{
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```