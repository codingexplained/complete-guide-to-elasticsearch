# Searching with wildcards

## Adding an asterisk for any characters (zero or more)

```
GET /product/_doc/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": "Veg*ble"
    }
  }
}
```

## Adding a question mark for any single character

```
GET /product/_doc/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": "Veg?ble"
    }
  }
}
```

```
GET /product/_doc/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": "Veget?ble"
    }
  }
}
```