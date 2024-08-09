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

## Importing data into local clusters

```
# Without CA certificate validation. This is fine for development clusters, but don't do this in production!
curl -k -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/products/_bulk --data-binary "@products-bulk.json"

# With CA certificate validation. The certificate is located at $ES_HOME/config/certs/http_ca.crt
curl --cacert /path/to/http_ca.crt -u elastic -H "Content-Type:application/x-ndjson" -XPOST https://localhost:9200/products/_bulk --data-binary "@products-bulk.json"
```

## Importing data into Elastic Cloud 

First, create an API key within Kibana (Stack Management > Security > API keys). Replace `API_TOKEN` below with the base64 encoded API key.

```bash
curl -H "Content-Type:application/x-ndjson" -H "Authorization:ApiKey API_TOKEN" -XPOST https://elastic-cloud-endpoint.com/products/_bulk --data-binary "@products-bulk.json"
```
