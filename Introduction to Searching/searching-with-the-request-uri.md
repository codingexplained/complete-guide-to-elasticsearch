# Searching with the request URI

## Matching all documents

```
GET /products/_search?q=*
```

## Matching documents containing the term `Lobster`

```
GET /products/_search?q=name:Lobster
```

## Matching documents containing the tag `Meat`

```
GET /products/_search?q=tags:Meat
```

## Matching documents containing the tag `Meat` _and_ name `Tuna`

```
GET /products/_search?q=tags:Meat AND name:Tuna
```