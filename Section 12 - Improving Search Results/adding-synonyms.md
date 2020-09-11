# Adding synonyms

## Creating index with custom analyzer

```
PUT /synonyms
{
  "settings": {
    "analysis": {
      "filter": {
        "synonym_test": {
          "type": "synonym", 
          "synonyms": [
            "awful => terrible",
            "awesome => great, super",
            "elasticsearch, logstash, kibana => elk",
            "weird, strange"
          ]
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

## Testing the analyzer (with synonyms)

```
POST /synonyms/_analyze
{
  "analyzer": "my_analyzer",
  "text": "awesome"
}
```

```
POST /synonyms/_analyze
{
  "analyzer": "my_analyzer",
  "text": "Elasticsearch"
}
```

```
POST /synonyms/_analyze
{
  "analyzer": "my_analyzer",
  "text": "weird"
}
```

```
POST /synonyms/_analyze
{
  "analyzer": "my_analyzer",
  "text": "Elasticsearch is awesome, but can also seem weird sometimes."
}
```

## Adding a test document

```
POST /synonyms/_doc
{
  "description": "Elasticsearch is awesome, but can also seem weird sometimes."
}
```

## Searching the index for synonyms

```
GET /synonyms/_search
{
  "query": {
    "match": {
      "description": "great"
    }
  }
}
```

```
GET /synonyms/_search
{
  "query": {
    "match": {
      "description": "awesome"
    }
  }
}
```