# Matching based on prefixes

## Matching documents containing a tag beginning with `Vege`

```
GET /product/default/_search
{
  "query": {
    "prefix": {
      "tags.keyword": "Vege"
    }
  }
}
```