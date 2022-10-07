# Missing field values

## Adding test documents

```
PUT /orders/_doc/1001
{
  "total_amount": 100
}
```

```
PUT /orders/_doc/1002
{
  "total_amount": 200,
  "status": null
}
```

## Aggregating documents with missing field value

```
GET /orders/_search
{
  "size": 0,
  "aggs": {
    "orders_without_status": {
      "missing": {
        "field": "status"
      }
    }
  }
}
```

## Combining `missing` aggregation with other aggregations

```
GET /orders/_search
{
  "size": 0,
  "aggs": {
    "orders_without_status": {
      "missing": {
        "field": "status"
      },
      "aggs": {
        "missing_sum": {
          "sum": {
            "field": "total_amount"
          }
        }
      }
    }
  }
}
```

## Deleting test documents

```
DELETE /orders/_doc/1001
```

```
DELETE /orders/_doc/1002
```