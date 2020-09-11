# Matching documents with non-null values

```
GET /product/_search
{
  "query": {
    "exists": {
      "field": "tags"
    }
  }
}
```