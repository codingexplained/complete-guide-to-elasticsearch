# Retrieving documents by IDs

```
GET /products/_search
{
  "query": {
    "ids": {
      "values": ["100", "200", "300"]
    }
  }
}
```