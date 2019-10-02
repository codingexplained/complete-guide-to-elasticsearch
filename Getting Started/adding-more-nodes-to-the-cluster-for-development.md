# Adding more nodes to the cluster (for development)

## Checking the cluster's health

```
GET /_cluster/health
```

## Checking the shard distribution

```
GET /_cat/shards?v
```

## Starting up a node from an existing node's directory

### macOS/Linux

```
bin/elasticsearch -E node.name=node-3 -E path.data=./node-3/data -E path.logs=./node-3/logs
```

### Windows

```
bin\elasticsearch.bat -E node.name=node-3 -E path.data=.\node-3\data -E path.logs=.\node-3\logs
```