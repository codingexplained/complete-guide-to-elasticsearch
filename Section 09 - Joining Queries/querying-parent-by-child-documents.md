# Querying parent by child documents

## Finding parents with child documents matching a `bool` query

```
GET /department/_search
{
  "query": {
    "has_child": {
      "type": "employee",
      "query": {
        "bool": {
          "must": [
            {
              "range": {
                "age": {
                  "gte": 50
                }
              }
            }
          ],
          "should": [
            {
              "term": {
                "gender.keyword": "M"
              }
            }
          ]
        }
      }
    }
  }
}
```

## Taking relevance scores into account with `score_mode`

```
GET /department/_search
{
  "query": {
    "has_child": {
      "type": "employee",
      "score_mode": "sum",
      "query": {
        "bool": {
          "must": [
            {
              "range": {
                "age": {
                  "gte": 50
                }
              }
            }
          ],
          "should": [
            {
              "term": {
                "gender.keyword": "M"
              }
            }
          ]
        }
      }
    }
  }
}
```

## Specifying the minimum and maximum number of children

```
GET /department/_search
{
  "query": {
    "has_child": {
      "type": "employee",
      "score_mode": "sum",
      "min_children": 2,
      "max_children": 5,
      "query": {
        "bool": {
          "must": [
            {
              "range": {
                "age": {
                  "gte": 50
                }
              }
            }
          ],
          "should": [
            {
              "term": {
                "gender.keyword": "M"
              }
            }
          ]
        }
      }
    }
  }
}
```