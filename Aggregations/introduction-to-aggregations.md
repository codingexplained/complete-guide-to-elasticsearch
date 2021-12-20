# Introduction to aggregations

## Adding `orders` index with field mappings

```
PUT /orders
{
  "mappings": {
    "properties": {
      "purchased_at": {
        "type": "date"
      },
      "lines": {
        "type": "nested",
        "properties": {
          "product_id": {
            "type": "integer"
          },
          "amount": {
            "type": "double"
          },
          "quantity": {
            "type": "short"
          }
        }
      },
      "total_amount": {
        "type": "double"
      },
      "status": {
        "type": "keyword"
      },
      "sales_channel": {
        "type": "keyword"
      },
      "salesman": {
        "type": "object",
        "properties": {
          "id": {
            "type": "integer"
          },
          "name": {
            "type": "text"
          }
        }
      }
    }
  }
}
```

## Populating the `orders` index with test data

```
curl -H "Content-Type:application/x-ndjson" -XPOST 'http://localhost:9200/orders/_bulk' --data-binary "@orders-bulk.json"
```
