# Searching with wildcards

## Adding an asterisk for any characters (zero or more)

```
GET /product/default/_search
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
GET /product/default/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": "Veg?ble"
    }
  }
}
```

```
GET /product/default/_search
{
  "query": {
    "wildcard": {
      "tags.keyword": "Veget?ble"
    }
  }
}
```