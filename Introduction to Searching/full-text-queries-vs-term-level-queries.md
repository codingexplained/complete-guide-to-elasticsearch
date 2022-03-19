# Full text queries vs term level queries

## Term level queries are not analyzed

```
GET /products/_search
{
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```

```
GET /products/_search
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
GET /products/_search
{
  "query": {
    "match": {
      "name": "Lobster"
    }
  }
}
```