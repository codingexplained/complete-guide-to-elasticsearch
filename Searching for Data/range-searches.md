# Range searches

## Basic usage

```
GET /products/_search
{
  "query": {
    "range": {
      "in_stock": {
        "gte": 1,
        "lte": 5
      }
    }
  }
}
```

**SQL:** `SELECT * FROM products WHERE in_stock >= 1 AND in_stock <= 5`

```
GET /products/_search
{
  "query": {
    "range": {
      "in_stock": {
        "gt": 1,
        "lt": 5
      }
    }
  }
}
```

**SQL:** `SELECT * FROM products WHERE in_stock > 1 AND in_stock < 5`

## Querying dates

### Basic usage

```
GET /products/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "2020/01/01",
        "lte": "2020/01/31"
      }
    }
  }
}
```

### Specifying the time

```
GET /products/_search
{
  "query": {
    "range": {
      "created": {
        "gte": "2020/01/01 00:00:00",
        "lte": "2020/01/31 23:59:59"
      }
    }
  }
}
```

### Specifying a UTC offset

```
GET /products/_search
{
  "query": {
    "range": {
      "created": {
        "time_zone": "+01:00",
        "gte": "2020/01/01 01:00:00",
        "lte": "2020/02/01 00:59:59"
      }
    }
  }
}
```

### Specifying a date format

```
GET /products/_search
{
  "query": {
    "range": {
      "created": {
        "format": "dd/MM/yyyy",
        "gte": "01/01/2020",
        "lte": "31/01/2020"
      }
    }
  }
}
```