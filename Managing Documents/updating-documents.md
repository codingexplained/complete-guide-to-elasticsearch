#1

POST /product/default/1/_update
{
  "doc": { "price": 95, "tags": [ "Elasticsearch" ] }
}

#2

GET /product/default/1