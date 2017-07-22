# Introducing the Query DSL

## Matching all documents

```
GET /product/default/_search
{
  "query": {
    "match_all": {}
  }
}
```