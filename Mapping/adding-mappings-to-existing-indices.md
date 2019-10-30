# Adding mappings to existing indices

## Adding mapping for `discount` field

```
PUT /product/_mapping
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
GET /product/_mapping
```