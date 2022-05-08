# Adding more nodes to the cluster (for development)

## Checking the cluster's health

```
GET /_cluster/health
```

## Checking the shard distribution

```
GET /_cat/shards?v
```

## Generating an enrollment token
When adding a new node to an existing Elasticsearch cluster, we first need to generate an enrollment token.

```
# macOS & Linux
bin/elasticsearch-create-enrollment-token --scope node

# Windows
bin\elasticsearch-create-enrollment-token.bat -s node
```

## Adding a new node to the cluster
To add a new node to an existing cluster, run the following command. Remember to have the working 
directory set to the new node's `$ES_HOME` directory (use the `cd` command for this).

```
# macOS & Linux
bin/elasticsearch --enrollment-token [INSERT_ENROLLMENT_TOKEN_HERE]

# Windows
bin\elasticsearch.bat --enrollment-token [INSERT_ENROLLMENT_TOKEN_HERE]
```

Once the node has been added, starting up the node again in the future is as simple as 
running `bin/elasticsearch` (macOS & Linux) or `bin\elasticsearch.bat` (Windows).