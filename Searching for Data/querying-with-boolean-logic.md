# Querying with boolean logic

## `must`

Query clauses added within the `must` occurrence type are required to match.

```
GET /products/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "term": {
            "tags.keyword": "Alcohol"
          }
        }
      ]
    }
  }
}
```

**SQL:** `SELECT * FROM products  WHERE tags IN ("Alcohol")`

## `must_not`

Query clauses added within the `must_not` occurrence type are required to _not_ match.

```
GET /products/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "term": {
            "tags.keyword": "Alcohol"
          }
        }
      ],
      "must_not": [
        {
          "term": {
            "tags.keyword": "Wine"
          }
        }
      ]
    }
  }
}
```

**SQL:** `SELECT * FROM products WHERE tags IN ("Alcohol") AND tags NOT IN ("Wine")`

## `should`

Matching query clauses within the `should` occurrence type boost a matching document's relevance score.

```
GET /products/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "term": {
            "tags.keyword": "Alcohol"
          }
        }
      ],
      "must_not": [
        {
          "term": {
            "tags.keyword": "Wine"
          }
        }
      ],
      "should": [
        {
          "term": {
            "tags.keyword": "Beer"
          }
        }
      ]
    }
  }
}
```

An example with a few more adding more `should` query clauses:

```
GET /products/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "term": {
            "tags.keyword": "Alcohol"
          }
        }
      ],
      "must_not": [
        {
          "term": {
            "tags.keyword": "Wine"
          }
        }
      ],
      "should": [
        {
          "term": {
            "tags.keyword": "Beer"
          }
        },
        {
          "match": {
            "name": "beer"
          }
        },
        {
          "match": {
            "description": "beer"
          }
        }
      ]
    }
  }
}
```

## `minimum_should_match`

Since only `should` query clauses are specified, at least one of them must match.

```
GET /products/_search
{
  "query": {
    "bool": {
      "should": [
        {
          "term": {
            "tags.keyword": "Beer"
          }
        },
        {
          "match": {
            "name": "beer"
          }
        }
      ]
    }
  }
}
```

Since a `must` query clause is specified, all of the `should` query clauses are optional. 
They are therefore only used to boost the relevance scores of matching documents.

```
GET /products/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "term": {
            "tags.keyword": "Alcohol"
          }
        }
      ], 
      "should": [
        {
          "term": {
            "tags.keyword": "Beer"
          }
        },
        {
          "match": {
            "name": "beer"
          }
        }
      ]
    }
  }
}
```

This behavior can be configured with the `minimum_should_match` parameter as follows.

```
GET /products/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "term": {
            "tags.keyword": "Alcohol"
          }
        }
      ], 
      "should": [
        {
          "term": {
            "tags.keyword": "Beer"
          }
        },
        {
          "match": {
            "name": "beer"
          }
        }
      ],
      "minimum_should_match": 1
    }
  }
}
```

## `filter`

Query clauses defined within the `filter` occurrence type must match. 
This is similar to the `must` occurrence type. The difference is that 
`filter` query clauses do not affect relevance scores and may be cached.

```
GET /products/_search
{
  "query": {
    "bool": {
      "filter": [
        {
          "term": {
            "tags.keyword": "Alcohol"
          }
        }
      ]
    }
  }
}
```

## Examples

### Example #1

**SQL:** `SELECT * FROM products WHERE (tags IN ("Beer") OR name LIKE '%Beer%') AND in_stock <= 100`

**Variation #1**

```
GET /products/_search
{
  "query": {
    "bool": {
      "filter": [
        {
          "range": {
            "in_stock": {
              "lte": 100
            }
          }
        }
      ],
      "must": [
        {
          "bool": {
            "should": [
              { "term": { "tags.keyword": "Beer" } },
              { "match": { "name": "Beer" } }
            ]
          }
        }
      ]
    }
  }
}
```

**Variation #2**

```
GET /products/_search
{
  "query": {
    "bool": {
      "filter": [
        {
          "range": {
            "in_stock": {
              "lte": 100
            }
          }
        }
      ],
      "should": [
        { "term": { "tags.keyword": "Beer" } },
        { "match": { "name": "Beer" } }
      ],
      "minimum_should_match": 1
    }
  }
}

```

### Example #2

**SQL:** `SELECT * FROM products WHERE tags IN ("Beer") AND (name LIKE '%Beer%' OR description LIKE '%Beer%') AND in_stock <= 100`

**Variation #1**

```
GET /products/_search
{
  "query": {
    "bool": {
      "filter": [
        {
          "range": {
            "in_stock": {
              "lte": 100
            }
          }
        },
        {
          "term": {
            "tags.keyword": "Beer"
          }
        }
      ],
      "should": [
        { "match": { "name": "Beer" } },
        { "match": { "description": "Beer" } }
      ],
      "minimum_should_match": 1
    }
  }
}
```

**Variation #2**

```
GET /products/_search
{
  "query": {
    "bool": {
      "filter": [
        {
          "range": {
            "in_stock": {
              "lte": 100
            }
          }
        },
        {
          "term": {
            "tags.keyword": "Beer"
          }
        }
      ],
      "must": [
        {
          "multi_match": {
            "query": "Beer",
            "fields": ["name", "description"]
          }
        }
      ]
    }
  }
}
```