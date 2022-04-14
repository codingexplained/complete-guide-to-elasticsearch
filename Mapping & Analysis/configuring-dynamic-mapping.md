# Configuring dynamic mapping

## Disable dynamic mapping
```
PUT /people
{
  "mappings": {
    "dynamic": false,
    "properties": {
      "first_name": {
        "type": "text"
      }
    }
  }
}
```

## Set dynamic mapping to `strict`
```
PUT /people
{
  "mappings": {
    "dynamic": "strict",
    "properties": {
      "first_name": {
        "type": "text"
      }
    }
  }
}
```

## Index a test document
```
POST /people/_doc
{
  "first_name": "Bo",
  "last_name": "Andersen"
}
```

## Retrieve mapping
```
GET /people/_mapping
```

## Search `first_name` field
```
GET /people/_search
{
  "query": {
    "match": {
      "first_name": "Bo"
    }
  }
}
```

## Search `last_name` field
```
GET /people/_search
{
  "query": {
    "match": {
      "last_name": "Andersen"
    }
  }
}
```

## Inheritance for the `dynamic` parameter
The following example sets the `dynamic` parameter to `"strict"` at the root level, but overrides it with a value of 
`true` for the `specifications.other` field mapping.

### Mapping
```
PUT /computers
{
  "mappings": {
    "dynamic": "strict",
    "properties": {
      "name": {
        "type": "text"
      },
      "specifications": {
        "properties": {
          "cpu": {
            "properties": {
              "name": {
                "type": "text"
              }
            }
          },
          "other": {
            "dynamic": true,
            "properties": { ... }
          }
        }
      }
    }
  }
}
```

### Example document (invalid)
```
POST /computers/_doc
{
  "name": "Gamer PC",
  "specifications": {
    "cpu": {
      "name": "Intel Core i7-9700K",
      "frequency": 3.6
    }
  }
}
```

### Example document (OK)
```
POST /computers/_doc
{
  "name": "Gamer PC",
  "specifications": {
    "cpu": {
      "name": "Intel Core i7-9700K"
    },
    "other": {
      "security": "Kensington"
    }
  }
}
```

## Enabling numeric detection
When enabling numeric detection, Elasticsearch will check the contents of strings to see if they contain only numeric 
values - and map the fields accordingly as either `float` or `long`.

### Mapping
```
PUT /computers
{
  "mappings": {
    "numeric_detection": true
  }
}
```

### Example document
```
POST /computers/_doc
{
  "specifications": {
    "other": {
      "max_ram_gb": "32", # long
      "bluetooth": "5.2" # float
    }
  }
}
```

## Date detection

### Disabling date detection
```
PUT /computers
{
  "mappings": {
    "date_detection": false
  }
}
```

### Configuring dynamic date formats
```
PUT /computers
{
  "mappings": {
    "dynamic_date_formats": ["dd-MM-yyyy"]
  }
}
```

## Clean up
```
DELETE /people
```