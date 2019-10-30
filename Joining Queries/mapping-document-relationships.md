# Mapping document relationships

```
PUT /department
{
  "mappings": {
    "properties": {
      "join_field": { 
        "type": "join",
        "relations": {
          "department": "employee"
        }
      }
    }
  }
}
```