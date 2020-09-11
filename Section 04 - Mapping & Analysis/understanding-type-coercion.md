# Understanding type coercion

## Supplying a floating point
```
PUT /coercion_test/_doc/1
{
  "price": 7.4
}
```

## Supplying a floating point within a string
```
PUT /coercion_test/_doc/2
{
  "price": "7.4"
}
```

## Supplying an invalid value
```
PUT /coercion_test/_doc/3
{
  "price": "7.4m"
}
```

## Retrieve document
```
GET /coercion_test/_doc/2
```

## Clean up
```
DELETE /coercion_test
```