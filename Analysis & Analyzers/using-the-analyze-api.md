# Using the `_analyze` API

## Tokenizing text with the `standard` tokenizer

```
POST _analyze
{
  "tokenizer": "standard",
  "text": "I'm in the mood for drinking semi-dry red wine!"
}
```

## Using the `lowercase` token filter

```
POST _analyze
{
  "filter": [ "lowercase" ],
  "text": "I'm in the mood for drinking semi-dry red wine!"
}
```

## Using the `standard` analyzer

```
POST _analyze
{
  "analyzer": "standard",
  "text": "I'm in the mood for drinking semi-dry red wine!"
}
```