# Replacing documents

## Replacing an existing document

```
PUT /product/_doc/1
{
  "name": "Complete Guide to Elasticsearch",
  "price": 195,
  "instructor": {
    "firstName": "Bo",
    "lastName": "Andersen"
  }
}
```

## Retrieving the replaced document

```
GET /product/_doc/1
```