# Adding documents

## Adding document with auto generated ID:

```
POST /product/_doc
{
  "name": "Processing Events with Logstash",
  "instructor": {
    "firstName": "Bo",
    "lastName": "Andersen"
  }
}
```

## Adding document by ID:

```
PUT /product/default/1
{
  "name": "Complete Guide to Elasticsearch",
  "instructor": {
    "firstName": "Bo",
    "lastName": "Andersen"
  }
}
```