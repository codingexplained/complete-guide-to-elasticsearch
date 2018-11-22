# Matching phrases

## The order of terms matters

```
GET /recipe/_doc/_search
{
  "query": {
    "match_phrase": {
      "title": "spaghetti puttanesca"
    }
  }
}
```

```
GET /recipe/_doc/_search
{
  "query": {
    "match_phrase": {
      "title": "puttanesca spaghetti"
    }
  }
}
```