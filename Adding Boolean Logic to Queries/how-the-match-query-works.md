# How the `match` query works

## The two queries below are equivalent

```
GET /recipe/default/_search
{
  "query": {
    "match": {
      "title": "pasta carbonara"
    }
  }
}
```

```
GET /recipe/default/_search
{
  "query": {
    "bool": {
      "should": [
        {
          "term": {
            "title": "pasta"
          }
        },
        {
          "term": {
            "title": "carbonara"
          }
        }
      ]
    }
  }
}
```

## The two queries below are equivalent

```
GET /recipe/default/_search
{
  "query": {
    "match": {
      "title": {
        "query": "pasta carbonara",
        "operator": "and"
      }
    }
  }
}
```

```
GET /recipe/default/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "term": {
            "title": "pasta"
          }
        },
        {
          "term": {
            "title": "carbonara"
          }
        }
      ]
    }
  }
}
```