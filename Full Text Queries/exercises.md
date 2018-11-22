# Exercises

```
GET /recipe/_doc/_search
{
  "query": {
    "match": {
      "title": "Pasta with parmesan and spinach"
    }
  }
}
```

```
GET /recipe/_doc/_search
{
  "query": {
    "match_phrase": {
      "title": "pasta carbonara"
    }
  }
}
```

```
GET /recipe/_doc/_search
{
  "query": {
    "match_phrase": {
      "title": "carbonara pasta"
    }
  }
}
```

```
GET /recipe/_doc/_search
{
  "query": {
    "multi_match": {
      "query": "pasta pesto",
      "fields": [ "title", "description" ]
    }
  }
}
```