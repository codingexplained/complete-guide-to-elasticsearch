# Prefixes, wildcards & regular expressions

## Searching for a prefix

```
GET /products/_search
{
  "query": {
    "prefix": {
      "name.keyword": {
        "value": "Past"
      }
    }
  }
}
```

## Wildcards

### Single character wildcard (`?`)

```
GET /products/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": {
        "value": "Past?"
      }
    }
  }
}
```

### Zero or more characters wildcard (`*`)

```
GET /products/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": {
        "value": "Bee*"
      }
    }
  }
}
```

## Regexp

```
GET /products/_search
{
  "query": {
    "regexp": {
      "tags.keyword": {
        "value": "Bee(f|r)+"
      }
    }
  }
}
```

## Case insensitive searches

All of the above queries can be made case insensitive by adding the `case_insensitive` parameter, e.g.:

```
GET /products/_search
{
  "query": {
    "prefix": {
      "name.keyword": {
        "value": "Past",
        "case_insensitive": true
      }
    }
  }
}
```