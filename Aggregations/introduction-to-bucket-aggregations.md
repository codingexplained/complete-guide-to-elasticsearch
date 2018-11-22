# Introduction to bucket aggregations

## Creating a bucket for each `status` value

```
GET /order/_doc/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status.keyword"
      }
    }
  }
}
```

## Including `20` terms instead of the default `10`

```
GET /order/_doc/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status.keyword",
        "size": 20
      }
    }
  }
}
```

## Aggregating documents with missing field (or `NULL`)

```
GET /order/_doc/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status.keyword",
        "size": 20,
        "missing": "N/A"
      }
    }
  }
}
```

## Changing the minimum document count for a bucket to be created

```
GET /order/_doc/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status.keyword",
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
GET /order/_doc/_search
{
  "size": 0,
  "aggs": {
    "status_terms": {
      "terms": {
        "field": "status.keyword",
        "size": 20,
        "missing": "N/A",
        "min_doc_count": 0,
        "order": {
          "_term": "asc"
        }
      }
    }
  }
}
```