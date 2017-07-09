# Updating documents

## Updating `price` field and adding `tags` field

```
POST /product/default/1/_update
{
  "doc": { "price": 95, "tags": [ "Elasticsearch" ] }
}
```

## Retrieving the updated document

```
GET /product/default/1
```