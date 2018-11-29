# Specifying an offset

## Specifying an offset with the `from` parameter

```
GET /recipe/default/_search
{
  "_source": false,
  "size": 2,
  "from": 2,
  "query": {
    "match": {
      "title": "pasta"
    }
  }
}
```