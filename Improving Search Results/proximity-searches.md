# Proximity searches

## Adding test documents

```
PUT /proximity/default/1
{
  "title": "Spicy Sauce"
}
```

```
PUT /proximity/default/2
{
  "title": "Spicy Tomato Sauce"
}
```

```
PUT /proximity/default/3
{
  "title": "Spicy Tomato and Garlic Sauce"
}
```

```
PUT /proximity/default/4
{
  "title": "Tomato Sauce (spicy)"
}
```

```
PUT /proximity/default/5
{
  "title": "Spicy and very delicious Tomato Sauce"
}
```

## Adding the `slop` parameter to a `match_phrase` query

```
GET /proximity/default/_search
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
GET /proximity/default/_search
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