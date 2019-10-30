# Introducing the Query DSL

## Matching all documents

```
GET /product/_search
{
  "query": {
    "match_all": {}
  }
}
```