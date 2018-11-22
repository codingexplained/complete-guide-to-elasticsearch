# Upserts

## Deleting the existing document

```
DELETE /product/_doc/1
```

## Inserting or updating a document (upsert)

```
POST /product/_doc/1/_update
{
    "script" : "ctx._source.price += 5",
    "upsert" : {
        "price" : 100
    }
}
```

## Retrieving the document

```
GET /product/_doc/1
```