# Querying by field existence

## Basic usage

```
GET /products/_search
{
  "query": {
    "exists": {
      "field": "tags.keyword"
    }
  }
}
```

**SQL:** `SELECT * FROM products WHERE tags IS NOT NULL`

## Inverting the query

There is no dedicated query for this, so we do it with the `bool` query.

```
GET /products/_search
{
  "query": {
    "bool": {
      "must_not": [
        {
          "exists": {
            "field": "tags.keyword"
          }
        }
      ]
    }
  }
}
```

**SQL:** `SELECT * FROM products WHERE tags IS NULL`