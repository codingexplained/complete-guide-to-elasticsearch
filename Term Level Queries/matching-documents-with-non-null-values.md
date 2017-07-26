# Matching documents with non-null values

```
GET /product/default/_search
{
  "query": {
    "exists": {
      "field": "tags"
    }
  }
}
```