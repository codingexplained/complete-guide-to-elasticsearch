# Terms lookup mechanism

## Adding test data

```
PUT /users/default/1
{
  "name": "John Roberts",
  "following" : [2, 3]
}
```

```
PUT /users/default/2
{
  "name": "Elizabeth Ross",
  "following" : []
}
```

```
PUT /users/default/3
{
  "name": "Jeremy Brooks",
  "following" : [1, 2]
}
```

```
PUT /users/default/4
{
  "name": "Diana Moore",
  "following" : [3, 1]
}
```

```
PUT /stories/default/1
{
  "user": 3,
  "content": "Wow look, a penguin!"
}
```

```
PUT /stories/default/2
{
  "user": 1,
  "content": "Just another day at the office... #coffee"
}
```

```
PUT /stories/default/3
{
  "user": 1,
  "content": "Making search great again! #elasticsearch #elk"
}
```

```
PUT /stories/default/4
{
  "user": 4,
  "content": "Had a blast today! #rollercoaster #amusementpark"
}
```

```
PUT /stories/default/5
{
  "user": 4,
  "content": "Yay, I just got hired as an Elasticsearch consultant - so excited!"
}
```

```
PUT /stories/default/6
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
                "type": "_doc",
                "id": 1,
                "path": "following"
            }
        }
    }
}
```