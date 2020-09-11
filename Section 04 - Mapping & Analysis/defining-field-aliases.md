# Defining field aliases

## Add `comment` alias pointing to the `content` field
```
PUT /reviews/_mapping
{
  "properties": {
    "comment": {
      "type": "alias",
      "path": "content"
    }
  }
}
```

## Using the field alias
```
GET /reviews/_search
{
  "query": {
    "match": {
      "comment": "outstanding"
    }
  }
}
```

## Using the "original" field name still works
```
GET /reviews/_search
{
  "query": {
    "match": {
      "content": "outstanding"
    }
  }
}
```