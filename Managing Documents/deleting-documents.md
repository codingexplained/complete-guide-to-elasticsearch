# Deleting documents

## Deleting document by ID

```
DELETE /product/_doc/1
```

## Adding test documents

```
POST /product/_doc
{
  "name": "Processing Events with Logstash",
  "category": "course"
}
```

```
POST /product/_doc
{
  "name": "The Art of Scalability",
  "category": "book"
}
```

## Deleting documents by query

```
POST /product/_delete_by_query
{
  "query": {
    "match": {
      "category": "book"
    }
  }
}
```