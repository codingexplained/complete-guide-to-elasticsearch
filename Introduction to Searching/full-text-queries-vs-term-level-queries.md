# Full text queries vs term level queries

## Term level queries are not analyzed

```
GET /product/default/_search
{
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```

```
GET /product/default/_search
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
GET /product/default/_search
{
  "query": {
    "match": {
      "name": "Lobster"
    }
  }
}
```