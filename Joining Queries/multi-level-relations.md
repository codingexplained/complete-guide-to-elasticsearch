# Multi-level relations

## Creating the index with mapping

```
PUT /company
{
  "mappings": {
    "_doc": {
      "properties": {
        "join_field": { 
          "type": "join",
          "relations": {
            "company": ["department", "supplier"],
            "department": "employee"
          }
        }
      }
    }
  }
}
```

## Adding a company

```
PUT /company/default/1
{
  "name": "My Company Inc.",
  "join_field": "company"
}
```

## Adding a department

```
PUT /company/default/2?routing=1
{
  "name": "Development",
  "join_field": {
    "name": "department",
    "parent": 1
  }
}
```

## Adding an employee

```
PUT /company/default/3?routing=1
{
  "name": "Bo Andersen",
  "join_field": {
    "name": "employee",
    "parent": 2
  }
}
```

## Adding some more test data
```
PUT /company/default/4
{
  "name": "Another Company, Inc.",
  "join_field": "company"
}
```

```
PUT /company/default/5?routing=4
{
  "name": "Marketing",
  "join_field": {
    "name": "department",
    "parent": 4
  }
}
```

```
PUT /company/default/6?routing=4
{
  "name": "John Doe",
  "join_field": {
    "name": "employee",
    "parent": 5
  }
}
```

## Example of querying multi-level relations

```
GET /company/_search
{
  "query": {
    "has_child": {
      "type": "department",
      "query": {
        "has_child": {
          "type": "employee",
          "query": {
            "term": {
              "name.keyword": "John Doe"
            }
          }
        }
      }
    }
  }
}
```