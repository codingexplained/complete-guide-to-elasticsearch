# Specifying the result format

## Returning results as YAML

```
GET /recipe/_doc/_search?format=yaml
{
    "query": {
      "match": { "title": "pasta" }
    }
}
```

## Returning pretty JSON

```
GET /recipe/_doc/_search?pretty
{
    "query": {
      "match": { "title": "pasta" }
    }
}
```