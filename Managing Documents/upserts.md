#1

DELETE /product/default/1

#2

POST /product/default/1/_update
{
    "script" : "ctx._source.price += 5",
    "upsert" : {
        "price" : 100
    }
}

#3

GET /product/default/1