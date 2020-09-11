# Adding synonyms from file

## Adding index with custom analyzer

```
PUT /synonyms
{
  "settings": {
    "analysis": {
      "filter": {
        "synonym_test": {
          "type": "synonym",
          "synonyms_path": "analysis/synonyms.txt"
        }
      },
      "analyzer": {
        "my_analyzer": {
          "tokenizer": "standard",
          "filter": [
            "lowercase",
            "synonym_test"
          ]
        }
      }
    }
  },
  "mappings": {
    "properties": {
      "description": {
        "type": "text",
        "analyzer": "my_analyzer"
      }
    }
  }
}
```

## Synonyms file (`config/analysis/synonyms.txt`)

```
# This is a comment

awful => terrible
awesome => great, super
elasticsearch, logstash, kibana => elk
weird, strange
```

## Testing the analyzer

```
POST /synonyms/_analyze
{
  "analyzer": "my_analyzer",
  "text": "Elasticsearch"
}
```