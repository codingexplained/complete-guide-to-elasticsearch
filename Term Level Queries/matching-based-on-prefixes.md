# Matching based on prefixes

## Matching documents containing a tag beginning with `Vege`

```
GET /product/_search
{
  "query": {
    "prefix": {
      "tags.keyword": "Vege"
    }
  }
}
```