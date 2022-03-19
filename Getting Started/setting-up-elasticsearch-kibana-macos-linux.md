# Setting up Elasticsearch & Kibana on macOS & Linux

## Extracting the archives

Both the Elasticsearch and Kibana archives can be extracted by using the below commands.
Alternatively, simply double-clicking them should do the trick.

```
cd /path/to/archive/directory
tar -zxf archive.tar.gz
```

## Starting up Elasticsearch

```
cd /path/to/elasticsearch
bin/elasticsearch
```

## Resetting the `elastic` user's password

If you lose the password for the `elastic` user, it can be reset with the following commands.

```
cd /path/to/elasticsearch
bin/elasticsearch-reset-password -u elastic
```

## Generating a new Kibana enrollment token

If you need to generate a new enrollment token for Kibana, this can be done with the following commands.

```
cd /path/to/elasticsearch
bin/elasticsearch-create-enrollment-token --scope kibana
```

## Disabling Gatekeeper for Kibana directory

macOS contains a security feature named Gatekeeper, which prevents Kibana from starting up.
We can disable it for just the Kibana directory, which allows Kibana to start up correctly.
Simply use the following command to do so.

```
xattr -d -r com.apple.quarantine /path/to/kibana
```

## Starting up Kibana

```
cd /path/to/kibana
bin/kibana
```