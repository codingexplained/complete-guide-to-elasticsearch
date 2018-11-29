# Picking up new fields without dynamic mapping

## Adding test document

```
POST /product/default/2000
{
  "description": "Test",
  "discount": 20
}
```

## Adding mapping for `discount` field

```
PUT /product/default/_mapping
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
GET /product/default/_search
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
GET /product/default/_search
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
DELETE /product/default/2000
```