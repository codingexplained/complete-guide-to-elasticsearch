# Matching documents with non-null values

```
GET /product/_doc/_search
{
  "query": {
    "exists": {
      "field": "tags"
    }
  }
}
```