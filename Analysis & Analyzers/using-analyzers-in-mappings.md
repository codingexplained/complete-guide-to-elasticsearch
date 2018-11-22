# Using analyzers in mappings

## Using a custom analyzer in field mappings

```
PUT /analyzers_test/_doc/_mapping
{
  "properties": {
    "description": {
      "type": "text",
      "analyzer": "my_analyzer"
    },
    "teaser": {
      "type": "text",
      "analyzer": "standard"
    }
  }
}
```

## Adding a test document

```
POST /analyzers_test/_doc/1
{
  "description": "drinking",
  "teaser": "drinking"
}
```

## Testing the mapping

```
GET /analyzers_test/_doc/_search
{
  "query": {
    "term": {
      "teaser": {
        "value": "drinking"
      }
    }
  }
}
```

```
GET /analyzers_test/_doc/_search
{
  "query": {
    "term": {
      "description": {
        "value": "drinking"
      }
    }
  }
}
```