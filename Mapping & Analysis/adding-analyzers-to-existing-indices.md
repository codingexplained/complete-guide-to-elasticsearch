# Adding analyzers to existing indices

## Close `analyzer_test` index
```
POST /analyzer_test/_close
```

## Add new analyzer
```
PUT /analyzer_test/_settings
{
  "analysis": {
    "analyzer": {
      "my_second_analyzer": {
        "type": "custom",
        "tokenizer": "standard",
        "char_filter": ["html_strip"],
        "filter": [
          "lowercase",
          "stop",
          "asciifolding"
        ]
      }
    }
  }
}
```

## Open `analyzer_test` index
```
POST /analyzer_test/_open
```

## Retrieve index settings
```
GET /analyzer_test/_settings
```