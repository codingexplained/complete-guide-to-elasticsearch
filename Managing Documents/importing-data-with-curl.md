# Importing data with cURL

## Navigating to bulk file directory

```
cd /path/to/data/file/directory
```

### Examples
```
# macOS and Linux
cd ~/Desktop

# Windows
cd C:\Users\[your_username]\Desktop
```

## Importing data into local cluster

```
curl --cacert [path_to_CA_certificate] -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/products/_bulk --data-binary "@products-bulk.json"

# Skipping the verification of the certificate (only for local development)
curl --insecure -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/products/_bulk --data-binary "@products-bulk.json"
```

## Importing data into Elastic Cloud 
```
curl -H "Content-Type:application/x-ndjson" -XPOST -u username:password https://elastic-cloud-endpoint.com:9243/products/_bulk --data-binary "@products-bulk.json"
```