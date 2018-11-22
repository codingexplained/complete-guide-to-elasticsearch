# How the `match` query works

## The two queries below are equivalent

```
GET /recipe/_doc/_search
{
  "query": {
    "match": {
      "title": "pasta carbonara"
    }
  }
}
```

```
GET /recipe/_doc/_search
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
GET /recipe/_doc/_search
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
GET /recipe/_doc/_search
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