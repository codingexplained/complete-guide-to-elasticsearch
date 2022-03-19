# Matching documents with non-null values

```
GET /products/_search
{
  "query": {
    "exists": {
      "field": "tags"
    }
  }
}
```