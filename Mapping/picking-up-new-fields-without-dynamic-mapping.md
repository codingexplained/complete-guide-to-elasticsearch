# Picking up new fields without dynamic mapping

## Adding test document

```
POST /product/_doc/2000
{
  "description": "Test",
  "discount": 20
}
```

## Adding mapping for `discount` field

```
PUT /product/_doc/_mapping
{
  "properties": {
    "discount": {
      "type": "integer"
    }
  }
}
```

## Querying the `description` field

```
GET /product/_doc/_search
{
  "query": {
    "match": {
      "description": "Test"
    }
  }
}
```

## Querying the `discount` field

```
GET /product/_doc/_search
{
  "query": {
    "term": {
      "discount": 20
    }
  }
}
```

## Picking up new mappings for documents

```
POST /product/_update_by_query?conflicts=proceed
```

## Deleting the test document

```
DELETE /product/_doc/2000
```