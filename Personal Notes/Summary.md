Build dashboards:
- System Administration
- Developers
- Management (KPIs, etc.)

We can use Elastic Search as an anlytics platform together with Kibana, it is perfectly valid and common use case.

Logstash
Process logs from applications and send them to Elasticsearch, but it has evolved into a more general purpose tool, meaning that Logstash is a data processing pipeline.
Logstash receives events from one or more inputs, processes them, and sends them to one or more stashes.

Basic Architecture of Elasticsearch
-----------------------------------
Elastichsearch is built in top of Apache Lucene.

When we started Elasticsearch, it starts a node. 
A node is an instance of Elasticsearch that stores data.

In production is recommended each node runs in a dedicated machine/VM/container.

A cluster is a collection of related nodes that together contain all of our data.

One cluster is tipally fair enough. But, we can have multiples clusters, each one dedicated to specific goal.

For instance, one cluster for powering the search of an e-commerce application and a 2nd one for Application Performance Management (APM)

Every document in Elasticsearch is stored in indexes.

An index groups documents together logically, as well as provide configuration options that are related to scalability and availability.

Elastic requests syntax:
* <http_verb> /<_api>/<command>

For example:
* GET /_cluster/health

* <_api> specifies the API that we want to access.
* Using _cat as <_api> value it means it is a CAT API, which outputs data into a human readable format
* APIs begins with an underscore by convetion.
* <command> specifies the command

System indices:
GET /_cat/indices?v&expand_wildcards=all

* System indices starts with "." (it means will be hidden by default, like in Linux filesystem), for instance: .geoip_databases, .tasks, etc.

Example by using curl:
curl -u elastic:59a5Ezy5VCv2666acRLuMJ2i -X GET -H "Content-Type:application/json" https://complete-guide-to-elasticsearch-65bc2f.es.us-central1.gcp.cloud.es.io/products/_search -d '{ "query": { "match_all": {} } }'

NOTES: For local deployments, specify either --insecure or --cacert

Sharding and scalability
-------------------------
* Sharding is a way to divide indices into smaller pieces
* Each piece is referred as a " shard"
* Sharding is done at the index level
* The main purpose is to horizontally scale the data volume

A bit deeper...
-> A shard is kind of an independent index
-> Each shard is an Apache Lucene index
-> An Ealsticsearch index consists of one or more Lucene indices
-> A shard has no predefined size; it grows as documents are added to it
-> A shard may store up to about two billions documents

Configuring the number of shards
* An index contains a single shard by default
* Indices in Elasticsearch < 7.0.0 were created with five shards




