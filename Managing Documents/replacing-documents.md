# Replacing documents

## Replacing an existing document

```
PUT /product/default/1
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
GET /product/default/1
```