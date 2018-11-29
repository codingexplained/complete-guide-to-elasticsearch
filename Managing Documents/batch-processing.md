# Batch processing

## Adding documents

```
POST /product/default/_bulk
{ "index": { "_id": "100" } }
{ "price": 100 }
{ "index": { "_id": "101" } }
{ "price": 101 }
```

## Updating and deleting documents

```
POST /product/default/_bulk
{ "update": { "_id": "100" } }
{ "doc": { "price": 1000 } }
{ "delete": { "_id": "101" } }
```

## Retrieving affected documents

```
GET /product/default/100
```

```
GET /product/default/101
```