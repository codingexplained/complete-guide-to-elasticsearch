# Terms lookup mechanism

## Adding test data

```
PUT /users/_doc/1
{
  "name": "John Roberts",
  "following" : [2, 3]
}
```

```
PUT /users/_doc/2
{
  "name": "Elizabeth Ross",
  "following" : []
}
```

```
PUT /users/_doc/3
{
  "name": "Jeremy Brooks",
  "following" : [1, 2]
}
```

```
PUT /users/_doc/4
{
  "name": "Diana Moore",
  "following" : [3, 1]
}
```

```
PUT /stories/_doc/1
{
  "user": 3,
  "content": "Wow look, a penguin!"
}
```

```
PUT /stories/_doc/2
{
  "user": 1,
  "content": "Just another day at the office... #coffee"
}
```

```
PUT /stories/_doc/3
{
  "user": 1,
  "content": "Making search great again! #elasticsearch #elk"
}
```

```
PUT /stories/_doc/4
{
  "user": 4,
  "content": "Had a blast today! #rollercoaster #amusementpark"
}
```

```
PUT /stories/_doc/5
{
  "user": 4,
  "content": "Yay, I just got hired as an Elasticsearch consultant - so excited!"
}
```

```
PUT /stories/_doc/6
{
  "user": 2,
  "content": "Chilling at the beach @ Greece #vacation #goodtimes"
}
```

## Querying stories from a user's followers

```
GET /stories/_search
{
  "query": {
    "terms": {
      "user": {
        "index": "users",
        "id": "1",
        "path": "following"
      }
    }
  }
}
```
