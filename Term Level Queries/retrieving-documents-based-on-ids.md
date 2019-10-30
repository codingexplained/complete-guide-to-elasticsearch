# Retrieving documents based on IDs

```
GET /product/_search
{
  "query": {
    "ids": {
      "values": [ 1, 2, 3 ]
    }
  }
}
```