# Sending queries with cURL

## Checking the cluster's health

```
GET /_cluster/health
```

## Test search query

```
GET /.kibana/_search
{
  "query": {
    "match_all": {}
  }
}
```