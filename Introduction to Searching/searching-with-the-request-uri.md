# Searching with the request URI

## Matching all documents

```
GET /product/_doc/_search?q=*
```

## Matching documents containing the term `Lobster`

```
GET /product/_doc/_search?q=name:Lobster
```

## Matching documents containing the tag `Meat`

```
GET /product/_doc/_search?q=tags:Meat
```

## Matching documents containing the tag `Meat` _and_ name `Tuna`

```
GET /product/_doc/_search?q=tags:Meat AND name:Tuna
```