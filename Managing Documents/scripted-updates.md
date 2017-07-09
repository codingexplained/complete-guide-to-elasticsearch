# Scripted updates

## Updating a document with a script

```
POST /product/default/1/_update
{
  "script" : "ctx._source.price += 10"
}
```

## Retrieving the updated document

```
GET /product/default/1
```