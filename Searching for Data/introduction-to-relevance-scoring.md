# Introduction to relevance scoring

The below query is the same as in the previous lecture, but here it is anyway for your convenience.

```
GET /products/_search
{
  "query": {
    "match": {
      "name": "pasta chicken"
    }
  }
}
```