# Updating documents

## Updating `price` field and adding `tags` field

```
POST /product/_doc/1/_update
{
  "doc": { "price": 95, "tags": [ "Elasticsearch" ] }
}
```

## Retrieving the updated document

```
GET /product/_doc/1
```