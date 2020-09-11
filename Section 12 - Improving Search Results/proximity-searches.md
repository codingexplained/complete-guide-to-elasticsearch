# Proximity searches

## Adding test documents

```
PUT /proximity/_doc/1
{
  "title": "Spicy Sauce"
}
```

```
PUT /proximity/_doc/2
{
  "title": "Spicy Tomato Sauce"
}
```

```
PUT /proximity/_doc/3
{
  "title": "Spicy Tomato and Garlic Sauce"
}
```

```
PUT /proximity/_doc/4
{
  "title": "Tomato Sauce (spicy)"
}
```

```
PUT /proximity/_doc/5
{
  "title": "Spicy and very delicious Tomato Sauce"
}
```

## Adding the `slop` parameter to a `match_phrase` query

```
GET /proximity/_search
{
  "query": {
    "match_phrase": {
      "title": {
        "query": "spicy sauce",
        "slop": 1
      }
    }
  }
}
```

```
GET /proximity/_search
{
  "query": {
    "match_phrase": {
      "title": {
        "query": "spicy sauce",
        "slop": 2
      }
    }
  }
}
```