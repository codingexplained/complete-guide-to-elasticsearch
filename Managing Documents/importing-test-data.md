#1

cd /path/to/data/file/directory

#2

curl -H "Content-Type: application/json" -XPOST 'http://localhost:9200/product/default/_bulk?pretty' --data-binary "@test-data.json"