# Mapping document relationships

```
PUT /department
{
  "mappings": {
    "_doc": {
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
}
```