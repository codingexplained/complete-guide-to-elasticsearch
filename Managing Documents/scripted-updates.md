#1

POST /product/default/1/_update
{
  "script" : "ctx._source.price += 10"
}

#2

GET /product/default/1