# Specifying the result format

## Returning results as YAML

```
GET /recipes/_search?format=yaml
{
    "query": {
      "match": { "title": "pasta" }
    }
}
```

## Returning pretty JSON

```
GET /recipes/_search?pretty
{
    "query": {
      "match": { "title": "pasta" }
    }
}
```