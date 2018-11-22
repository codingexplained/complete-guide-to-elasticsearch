# Importing test data

## Navigating to bulk file directory

```
cd /path/to/data/file/directory
```

## Importing test data with cURL

```
curl -H "Content-Type: application/json" -XPOST 'http://localhost:9200/product/_doc/_bulk?pretty' --data-binary "@products-bulk.json"
```