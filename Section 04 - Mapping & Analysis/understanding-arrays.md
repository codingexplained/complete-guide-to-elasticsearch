# Understanding arrays

## Arrays of strings are concatenated when analyzed
```
POST /_analyze
{
  "text": ["Strings are simply", "merged together."],
  "analyzer": "standard"
}
```