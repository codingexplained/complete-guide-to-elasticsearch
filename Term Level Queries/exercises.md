# Exercises

## Matching documents with a `sold` field of less than `10`

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "sold": {
        "lt": 10
      }
    }
  }
}
```

## Matching documents with a `sold` field between `10` (inclusive) and `30` (exclusive)

```
GET /product/_doc/_search
{
  "query": {
    "range": {
      "sold": {
        "lt": 30,
        "gte": 10
      }
    }
  }
}
```

## Matching documents containing the tag `Meat`

```
GET /product/_doc/_search
{
  "query": {
    "term": {
      "tags.keyword": "Meat"
    }
  }
}
```

## Matching documents containing `Tomato` or `Paste` within the `name` field

```
GET /product/_doc/_search
{
  "query": {
    "terms": {
      "name": [ "Tomato", "Paste" ]
    }
  }
}
```

## Matching documents containing `past` followed by an optional character, for the `name` field

```
GET /product/_doc/_search
{
  "query": {
    "wildcard": {
      "name": "past?"
    }
  }
}
```

## Matching documents containing a number within the `name` field

```
GET /product/_doc/_search
{
  "query": {
    "regexp": {
      "name": "[0-9]+"
    }
  }
}
```
