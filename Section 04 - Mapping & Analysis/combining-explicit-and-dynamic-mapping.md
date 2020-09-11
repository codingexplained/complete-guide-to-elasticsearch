# Combining explicit and dynamic mapping

## Create index with one field mapping
```
PUT /people
{
  "mappings": {
    "properties": {
      "first_name": {
        "type": "text"
      }
    }
  }
}
```

## Index a test document with an unmapped field
```
POST /people/_doc
{
  "first_name": "Bo",
  "last_name": "Andersen"
}
```

## Retrieve mapping
```
GET /people/_mapping
```

## Clean up
```
DELETE /people
```