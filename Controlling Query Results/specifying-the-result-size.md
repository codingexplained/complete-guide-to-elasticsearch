# Specifying the result size

## Using a query parameter

```
GET /recipe/default/_search?size=2
{
  "_source": false,
  "query": {
    "match": {
      "title": "pasta"
    }
  }
}
```

## Using a parameter within the request body

```
GET /recipe/default/_search
{
  "_source": false,
  "size": 2,
  "query": {
    "match": {
      "title": "pasta"
    }
  }
}
```