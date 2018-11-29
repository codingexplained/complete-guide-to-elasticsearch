# Adding documents

## Adding departments

```
PUT /department/default/1
{
  "name": "Development",
  "join_field": "department"
}
```

```
PUT /department/default/2
{
  "name": "Marketing",
  "join_field": "department"
}
```

## Adding employees for departments

```
PUT /department/default/3?routing=1
{
  "name": "Bo Andersen",
  "age": 28,
  "gender": "M",
  "join_field": {
    "name": "employee",
    "parent": 1
  }
}
```

```
PUT /department/default/4?routing=2
{
  "name": "John Doe",
  "age": 44,
  "gender": "M",
  "join_field": {
    "name": "employee",
    "parent": 2
  }
}
```

```
PUT /department/default/5?routing=1
{
  "name": "James Evans",
  "age": 32,
  "gender": "M",
  "join_field": {
    "name": "employee",
    "parent": 1
  }
}
```

```
PUT /department/default/6?routing=1
{
  "name": "Daniel Harris",
  "age": 52,
  "gender": "M",
  "join_field": {
    "name": "employee",
    "parent": 1
  }
}
```

```
PUT /department/default/7?routing=2
{
  "name": "Jane Park",
  "age": 23,
  "gender": "F",
  "join_field": {
    "name": "employee",
    "parent": 2
  }
}
```

```
PUT /department/default/8?routing=1
{
  "name": "Christina Parker",
  "age": 29,
  "gender": "F",
  "join_field": {
    "name": "employee",
    "parent": 1
  }
}
```