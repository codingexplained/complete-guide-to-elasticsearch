# Searching for a term

## Matching documents with a value of `true` for the `is_active` field

```
GET /products/_search
{
  "query": {
    "term": {
      "is_active": true
    }
  }
}
```

```
GET /products/_search
{
  "query": {
    "term": {
      "is_active": {
        "value": true
      }
    }
  }
}
```