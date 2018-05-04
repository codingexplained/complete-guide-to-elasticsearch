# Understanding relevance scores

```
GET /product/default/_search
{
  "explain": true,
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```