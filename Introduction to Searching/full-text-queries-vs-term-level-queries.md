# Full text queries vs term level queries

## Term level queries are not analyzed

```
GET /product/_doc/_search
{
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```

```
GET /product/_doc/_search
{
  "query": {
    "term": {
      "name": "Lobster"
    }
  }
}
```

## Full-text queries are analyzed

```
GET /product/_doc/_search
{
  "query": {
    "match": {
      "name": "Lobster"
    }
  }
}
```