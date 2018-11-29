# Retrieving documents based on IDs

```
GET /product/default/_search
{
  "query": {
    "ids": {
      "values": [ 1, 2, 3 ]
    }
  }
}
```