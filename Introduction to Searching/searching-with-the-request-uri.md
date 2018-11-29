# Searching with the request URI

## Matching all documents

```
GET /product/default/_search?q=*
```

## Matching documents containing the term `Lobster`

```
GET /product/default/_search?q=name:Lobster
```

## Matching documents containing the tag `Meat`

```
GET /product/default/_search?q=tags:Meat
```

## Matching documents containing the tag `Meat` _and_ name `Tuna`

```
GET /product/default/_search?q=tags:Meat AND name:Tuna
```