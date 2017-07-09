# Adding mappings to existing indices

## Adding mapping for `discount` field

```
PUT /product/default/_mapping
{
  "properties": {
    "discount": {
      "type": "double"
    }
  }
}
```

## Retrieving mapping

```
GET /product/default/_mapping
```