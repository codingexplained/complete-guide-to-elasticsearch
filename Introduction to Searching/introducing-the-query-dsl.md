# Introducing the Query DSL

## Matching all documents

```
GET /product/_doc/_search
{
  "query": {
    "match_all": {}
  }
}
```