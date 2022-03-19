# Setting up Elasticsearch & Kibana on Windows

## Starting up Elasticsearch

```
cd path\to\elasticsearch
bin\elasticsearch.bat
```

## Resetting the `elastic` user's password

If you lose the password for the `elastic` user, it can be reset with the following commands.

```
cd path\to\elasticsearch
bin\elasticsearch-reset-password.bat -u elastic
```

## Generating a new Kibana enrollment token

If you need to generate a new enrollment token for Kibana, this can be done with the following commands.

```
cd path\to\elasticsearch
bin\elasticsearch-create-enrollment-token.bat -s kibana
```

## Starting up Kibana

```
cd path\to\kibana
bin\kibana.bat
```