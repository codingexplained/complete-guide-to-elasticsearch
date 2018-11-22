# Working with relative dates

## Subtracting one year from `2010/01/01`

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "2010/01/01||-1y"
      }
    }
  }
}
```

## Subtracting one year and one day from `2010/01/01`

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "2010/01/01||-1y-1d"
      }
    }
  }
}
```

## Subtracting one year from `2010/01/01` and rounding by month

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "2010/01/01||-1y/M"
      }
    }
  }
}
```

## Rounding by month _before_ subtracting one year from `2010/01/01`

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "2010/01/01||/M-1y"
      }
    }
  }
}
```

## Rounding by month _before_ subtracting one year from the current date

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "now/M-1y"
      }
    }
  }
}
```

## Matching documents with a `created` field containing the current date or later

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "now"
      }
    }
  }
}
```