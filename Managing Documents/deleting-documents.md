#1

DELETE /product/default/1

#2

POST /product/default
{
  "name": "Processing Events with Logstash",
  "category": "course"
}

#3

POST /product/default
{
  "name": "The Art of Scalability",
  "category": "book"
}

#4

POST /product/_delete_by_query
{
  "query": {
    "match": {
      "category": "book"
    }
  }
}