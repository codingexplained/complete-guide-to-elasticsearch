# Debugging unexpected query results

```
GET /product/_doc/1/_explain
{
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```
# 8.0 syntax

```
GET /product/_explain/1
{
  "query": {
    "term": {
      "name": "lobster"
    }
  }
}
```
