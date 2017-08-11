# Specifying the result format

## Returning results as YAML

```
GET /recipe/default/_search?format=yaml
{
    "query": {
      "match": { "title": "pasta" }
    }
}
```

## Returning pretty JSON

```
GET /recipe/default/_search?pretty
{
    "query": {
      "match": { "title": "pasta" }
    }
}
```