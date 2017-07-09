# Exploring the cluster

## Checking the cluster health

```
GET /_cat/health?v
```

## Listing the cluster's nodes

```
GET /_cat/nodes?v
```

## Listing the cluster's indices

```
GET /_cat/indices?v
```

## Checking the shard allocation

```
GET /_cat/allocation?v
```

## Checking which nodes contain which shards

```
GET /_cat/shards?v
```