# Understanding relevance scores

```
GET /product/default/_search?explain
{
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```