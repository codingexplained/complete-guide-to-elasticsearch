# Multi-field mappings

## Add `keyword` mapping to a `text` field
```
PUT /multi_field_test
{
  "mappings": {
    "properties": {
      "description": {
        "type": "text"
      },
      "ingredients": {
        "type": "text",
        "fields": {
          "keyword": {
            "type": "keyword"
          }
        }
      }
    }
  }
}
```

## Index a test document
```
POST /multi_field_test/_doc
{
  "description": "To make this spaghetti carbonara, you first need to...",
  "ingredients": ["Spaghetti", "Bacon", "Eggs"]
}
```

## Retrieve documents
```
GET /multi_field_test/_search
{
  "query": {
    "match_all": {}
  }
}
```

## Querying the `text` mapping
```
GET /multi_field_test/_search
{
  "query": {
    "match": {
      "ingredients": "Spaghetti"
    }
  }
}
```

## Querying the `keyword` mapping
```
GET /multi_field_test/_search
{
  "query": {
    "term": {
      "ingredients.keyword": "Spaghetti"
    }
  }
}
```

## Clean up
```
DELETE /multi_field_test
```