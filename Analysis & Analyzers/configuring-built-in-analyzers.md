# Configuring built-in analyzers

## Configuring the `standard` analyzer

```
PUT /analyzers_test
{
  "settings": {
    "analysis": {
      "analyzer": {
        "english_stop": {
          "type": "standard",
          "stopwords": "_english_"
        }
      },
      "filter": {
        "my_stemmer": {
          "type": "stemmer",
          "name": "english"
        }
      }
    }
  }
}
```

## Testing the custom analyzer

```
POST /analyzers_test/_analyze
{
  "analyzer": "english_stop",
  "text": "I'm in the mood for drinking semi-dry red wine!"
}
```

```
POST /analyzers_test/_analyze
{
  "tokenizer": "standard",
  "filter": [ "my_stemmer" ],
  "text": "I'm in the mood for drinking semi-dry red wine!"
}
```