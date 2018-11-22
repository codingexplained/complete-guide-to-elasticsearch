# Matching documents with range values

## Matching documents with an `in_stock` field of between `1` and `5`, both included

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "in_stock": {
        "gte": 1,
        "lte": 5
      }
    }
  }
}
```

## Matching documents with a date range

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "2010/01/01",
        "lte": "2010/12/31"
      }
    }
  }
}
```

## Matching documents with a date range and custom date format

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "01-01-2010",
        "lte": "31-12-2010",
        "format": "dd-MM-yyyy"
      }
    }
  }
}
```