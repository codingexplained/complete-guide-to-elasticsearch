# Adding mappings to existing indices

## Add new field mapping to existing index
```
PUT /reviews/_mapping
{
  "properties": {
    "created_at": {
      "type": "date"
    }
  }
}
```

## Retrieve the mapping
```
GET /reviews/_mapping
```