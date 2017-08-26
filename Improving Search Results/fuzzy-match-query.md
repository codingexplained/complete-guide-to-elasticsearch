# Fuzzy `match` query

## Searching with `fuzziness` set to `auto`

```
GET /product/default/_search
{
  "query": {
    "match": {
      "name": {
        "query": "l0bster",
        "fuzziness": "auto"
      }
    }
  }
}
```

```
GET /product/default/_search
{
  "query": {
    "match": {
      "name": {
        "query": "lobster",
        "fuzziness": "auto"
      }
    }
  }
}
```

## Fuzziness is per term (and specifying an integer)

```
GET /product/default/_search
{
  "query": {
    "match": {
      "name": {
        "query": "l0bster love",
        "operator": "and",
        "fuzziness": 1
      }
    }
  }
}
```

## Switching letters around with transpositions

```
GET /product/default/_search
{
  "query": {
    "match": {
      "name": {
        "query": "lvie",
        "fuzziness": 1
      }
    }
  }
}
```

## Disabling transpositions

```
GET /product/default/_search
{
  "query": {
    "match": {
      "name": {
        "query": "lvie",
        "fuzziness": 1,
        "fuzzy_transpositions": false
      }
    }
  }
}
```