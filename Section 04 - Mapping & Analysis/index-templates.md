# Index templates

## Adding an index template named `access-logs`
```
PUT /_template/access-logs
{
  "index_patterns": ["access-logs-*"],
  "settings": {
    "number_of_shards": 2,
    "index.mapping.coerce": false
  }, 
  "mappings": {
    "properties": {
      "@timestamp": {
        "type": "date"
      },
      "url.original": {
        "type": "keyword"
      },
      "http.request.referrer": {
        "type": "keyword"
      },
      "http.response.status_code": {
        "type": "long"
      }
    }
  }
}
```

## Adding an index matching the index template's pattern
```
PUT /access-logs-2020-01-01
```

## Verify that the mapping is applied
```
GET /access-logs-2020-01-01
```