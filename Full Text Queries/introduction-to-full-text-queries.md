# Introduction to full text queries

## Importing new test data

```shell
cd /path/to/data/file/directory
```

```shell
curl -H "Content-Type: application/json" -XPOST 'http://localhost:9200/recipe/_doc/_bulk?pretty' --data-binary "@test-data.json"
```

## Inspecting the mapping

```
GET /recipe/_doc/_mapping
```