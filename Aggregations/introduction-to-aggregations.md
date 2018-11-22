# Introduction to aggregations

## Adding `order` index and mappings

```
PUT /order
{
  "mappings": {
    "_doc": {
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
}
```

## Populating the `order` index with test data

```
curl -H "Content-Type: application/json" -XPOST 'http://localhost:9200/order/_doc/_bulk?pretty' --data-binary "@orders-bulk.json"
```