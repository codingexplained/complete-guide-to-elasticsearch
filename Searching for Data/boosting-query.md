# Boosting query

## Matching juice products

```
GET /products/_search
{
  "size": 20,
  "query": {
    "match": {
      "name": "juice"
    }
  }
}
```

## Match juice products, but deprioritize apple juice

```
GET /products/_search
{
  "size": 20,
  "query": {
    "boosting": {
      "positive": {
        "match": {
          "name": "juice"
        }
      },
      "negative": {
        "match": {
          "name": "apple"
        }
      },
      "negative_boost": 0.5
    }
  }
}
```

## Without filtering (deprioritize everything apples)

```
GET /products/_search
{
  "query": {
    "boosting": {
      "positive": {
        "match_all": {}
      },
      "negative": {
        "match": {
          "name": "apple"
        }
      },
      "negative_boost": 0.5
    }
  }
}
```

## More examples

### "I like pasta"

Boost the relevance scores for pasta products.

```
GET /recipes/_search
{
  "query": {
    "bool": {
      "must": [
        { "match_all": {} }
      ], 
      "should": [
        {
          "term": {
            "ingredients.name.keyword": "Pasta"
          }
        }
      ]
    }
  }
}
```

### "I don't like bacon"

Reduce the relevance scores for bacon products.

```
GET /recipes/_search
{
  "query": {
    "boosting": {
      "positive": {
        "match_all": {}
      },
      "negative": {
        "term": {
          "ingredients.name.keyword": "Bacon"
        }
      },
      "negative_boost": 0.5
    }
  }
}
```

### Pasta products, preferably without bacon

```
GET /recipes/_search
{
  "query": {
    "boosting": {
      "positive": {
        "term": {
          "ingredients.name.keyword": "Pasta"
        }
      },
      "negative": {
        "term": {
          "ingredients.name.keyword": "Bacon"
        }
      },
      "negative_boost": 0.5
    }
  }
}
```

### "I like pasta, but not bacon"

```
GET /recipes/_search
{
  "query": {
    "boosting": {
      "positive": {
        "bool": {
          "must": [
            { "match_all": {} }
          ],
          "should": [
            {
              "term": {
                "ingredients.name.keyword": "Pasta"
              }
            }
          ]
        }
      },
      "negative": {
        "term": {
          "ingredients.name.keyword": "Bacon"
        }
      },
      "negative_boost": 0.5
    }
  }
}
```