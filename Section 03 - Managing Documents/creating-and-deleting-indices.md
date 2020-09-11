# Creating & Deleting Indices

## Deleting an index

```
DELETE /pages
```

## Creating an index (with settings)

```
PUT /products
{
  "settings": {
    "number_of_shards": 2,
    "number_of_replicas": 2
  }
}
```