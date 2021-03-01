# Introducing the Query DSL

## Matching all documents

```
GET /products/_search
{
  "query": {
    "match_all": {}
  }
}
```