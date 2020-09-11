# Exercises

```
GET /recipe/_search
{
  "query": {
    "match": {
      "title": "Pasta with parmesan and spinach"
    }
  }
}
```

```
GET /recipe/_search
{
  "query": {
    "match_phrase": {
      "title": "pasta carbonara"
    }
  }
}
```

```
GET /recipe/_search
{
  "query": {
    "match_phrase": {
      "title": "carbonara pasta"
    }
  }
}
```

```
GET /recipe/_search
{
  "query": {
    "multi_match": {
      "query": "pasta pesto",
      "fields": [ "title", "description" ]
    }
  }
}
```