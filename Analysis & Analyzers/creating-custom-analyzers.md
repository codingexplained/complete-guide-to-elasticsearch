# Creating custom analyzers

## Adding a custom analyzer

```
PUT /analyzers_test
{
  "settings": {
    "analysis": {
      "filter": {
        "my_stemmer": {
          "type": "stemmer",
          "name": "english"
        }
      },
      "analyzer": {
        "english_stop": {
          "type": "standard",
          "stopwords": "_english_"
        },
        "my_analyzer": {
          "type": "custom",
          "tokenizer": "standard",
          "char_filter": [
            "html_strip"
          ],
          "filter": [
            "lowercase",
            "trim",
            "my_stemmer"
          ]
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
  "analyzer": "my_analyzer",
  "text": "I'm in the mood for drinking <strong>semi-dry</strong> red wine!"
}
```