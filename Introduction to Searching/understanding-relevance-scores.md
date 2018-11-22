# Understanding relevance scores

```
GET /product/_doc/_search
{
  "explain": true,
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```