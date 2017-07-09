#1

POST /product/default/_bulk
{ "index": { "_id": "100" } }
{ "price": 100 }
{ "index": { "_id": "101" } }
{ "price": 101 }

#2

POST /product/default/_bulk
{ "update": { "_id": "100" } }
{ "doc": { "price": 1000 } }
{ "delete": { "_id": "101" } }

#3

GET /product/default/100

#4

GET /product/default/101