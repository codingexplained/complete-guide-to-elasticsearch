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

If you are using a cloud hosted Elasticsearch deployment, remove the `--cacert` argument.

```
# macOS & Linux
curl --cacert config/certs/http_ca.crt -u elastic -H "Content-Type:application/x-ndjson" -X POST https://localhost:9200/orders/_bulk --data-binary "@orders-bulk.json"

# Windows
curl --cacert config\certs\http_ca.crt -u elastic -H "Content-Type:application/x-ndjson" -X POST https://localhost:9200/orders/_bulk --data-binary "@orders-bulk.json"
```