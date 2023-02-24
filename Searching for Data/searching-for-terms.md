# Searching for terms

## Basic usage

```
GET /products/_search
{
  "query": {
    "term": {
      "tags.keyword": "Vegetable"
    }
  }
}
```

## Explicit syntax

A more explicit syntax than the above. Use this if you need to add parameters to the query.

```
GET /products/_search
{
  "query": {
    "term": {
      "tags.keyword": {
        "value": "Vegetable"
      }
    }
  }
}
```

## Case insensitive search

```
GET /products/_search
{
  "query": {
    "term": {
      "tags.keyword": {
        "value": "Vegetable",
        "case_insensitive": true
      }
    }
  }
}
```

## Searching for multiple terms

```
GET /products/_search
{
  "query": {
    "terms": {
      "tags.keyword": ["Soup", "Meat"]
    }
  }
}
```

## Searching for booleans

```
GET /products/_search
{
  "query": {
    "term": {
      "is_active": true
    }
  }
}
```

## Searching for numbers

```
GET /products/_search
{
  "query": {
    "term": {
      "in_stock": 1
    }
  }
}
```

## Searching for dates

```
GET /products/_search
{
  "query": {
    "term": {
      "created": "2007/10/14"
    }
  }
}
```

## Searching for timestamps

```
GET /products/_search
{
  "query": {
    "term": {
      "created": "2007/10/14 12:34:56"
    }
  }
}
```