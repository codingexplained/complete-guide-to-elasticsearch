# Missing field values

## Adding test documents

```
POST /order/default/1001
{
  "total_amount": 100
}
```

```
POST /order/default/1002
{
  "total_amount": 200,
  "status": null
}
```

## Aggregating documents with missing field value

```
GET /order/default/_search
{
  "size": 0,
  "aggs": {
    "orders_without_status": {
      "missing": {
        "field": "status.keyword"
      }
    }
  }
}
```

## Combining `missing` aggregation with other aggregations

```
GET /order/default/_search
{
  "size": 0,
  "aggs": {
    "orders_without_status": {
      "missing": {
        "field": "status.keyword"
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
DELETE /order/default/1001
```

```
DELETE /order/default/1002
```