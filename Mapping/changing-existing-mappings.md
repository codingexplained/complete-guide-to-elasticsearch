# Changing existing mappings

## Deleting the index

```
DELETE /product
```

## Creating index with mappings

```
PUT /product
{
  "mappings": {
    "dynamic": false,
    "properties": {
      "in_stock": {
        "type": "integer"
      },
      "is_active": {
        "type": "boolean"
      },
      "price": {
        "type": "integer"
      },
      "sold": {
        "type": "long"
      }
    }
  }
}
```