# Defining custom date formats

## Date mapping with `year` format

```
PUT /product/_doc/_mapping
{
  "properties": {
    "created": {
      "type": "date",
      "format": "year"
    }
  }
}
```

## Date mapping with `strict_year` format

```
PUT /product/_doc/_mapping
{
  "properties": {
    "created": {
      "type": "date",
      "format": "strict_year"
    }
  }
}
```

## Date mapping with explicit default format

```
PUT /product/_doc/_mapping
{
  "properties": {
    "created": {
      "type": "date",
      "format": "strict_date_optional_time||epoch_millis"
    }
  }
}
```

## Date mapping with date and optional time

```
PUT /product/_doc/_mapping
{
  "properties": {
    "created": {
      "type": "date",
      "format": "yyyy/MM/dd HH:mm:ss||yyyy/MM/dd"
    }
  }
}
```