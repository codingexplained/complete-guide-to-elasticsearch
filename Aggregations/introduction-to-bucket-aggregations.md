# Introduction to bucket aggregations

## Creating a bucket for each `status` value

```
GET /orders/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status"
      }
    }
  }
}
```

## Including `20` terms instead of the default `10`

```
GET /orders/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status",
        "size": 20
      }
    }
  }
}
```

## Aggregating documents with missing field (or `NULL`)

```
GET /orders/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status",
        "size": 20,
        "missing": "N/A"
      }
    }
  }
}
```

## Changing the minimum document count for a bucket to be created

```
GET /orders/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status",
        "size": 20,
        "missing": "N/A",
        "min_doc_count": 0
      }
    }
  }
}
```

## Ordering the buckets

```
GET /orders/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status",
        "size": 20,
        "missing": "N/A",
        "min_doc_count": 0,
        "order": {
          "_key": "asc"
        }
      }
    }
  }
}
```