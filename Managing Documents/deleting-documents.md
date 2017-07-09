# Deleting documents

## Deleting document by ID

```
DELETE /product/default/1
```

## Adding test documents

```
POST /product/default
{
  "name": "Processing Events with Logstash",
  "category": "course"
}
```

```
POST /product/default
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