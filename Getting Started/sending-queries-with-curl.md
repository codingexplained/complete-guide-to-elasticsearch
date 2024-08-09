# Sending queries with cURL

## Handling self signed certificates

Local deployments of Elasticsearch are protected with a self signed certificate by default, which HTTP clients do not trust. 
Sending a request will therefore fail with a certificate error. To fix this, we have a couple of options. 
For cloud deployments, simply skip this step.

### 1. Skip certificate verification

One option is to entirely skip the verification of the certificate. This is not exactly best practice, 
but if you are just developing with a local cluster, then it might be just fine. To ignore the 
certificate, use either the `--insecure` flag or `-k`.

```
curl --insecure [...]
curl -k [...]
```

### 2. Provide the CA certificate

A better approach is to provide the CA certificate so that the TLS certificate is not just ignored. 
The path to the file can be supplied with the `--cacert` argument. The CA certificate is typically stored within 
the `config/certs` directory, although the `certs` directory may be at the root of your Elasticsearch 
home directory (`$ES_HOME`) depending on how you installed Elasticsearch.

```
# macOS & Linux
cd /path/to/elasticsearch
curl --cacert config/certs/http_ca.crt [...]

# Windows
cd C:\Path\To\Elasticsearch
curl --cacert config\certs\http_ca.crt [...]
```

Alternatively, you can specify the absolute path to the file.

## Authentication
All requests made to Elasticsearch must be authenticated by default.

### Local deployments
For local deployments, use the password that was generated for the `elastic` user the first time Elasticsearch started up.

```
curl -u elastic [...]
```

The above will prompt you to enter the password when running the command. Alternatively, you can enter 
the password directly within the command as follows (without the brackets).

```
curl -u elastic:[YOUR_PASSWORD_HERE] [...]
```

Note that this exposes your password within the terminal, so this is not best practice from a security perspective.

### Elastic Cloud
With Elastic Cloud, we should add an `Authorization` header to our requests and include an API key. API keys can be 
created within Kibana (Stack Management > Security > API keys). Replace `API_TOKEN` below with the base64 encoded API key.

```bash
curl -H "Authorization:ApiKey API_TOKEN" [...]
```

## Adding a request body & `Content-Type` header

To send data within the request, use the `-d` argument, e.g. for the `match_all` query. Note that using 
single quotes does not work on Windows, so each double quote within the JSON object must be escaped.

```
# macOS & Linux
curl [...] https://localhost:9200/products/_search -d '{ "query": { "match_all": {} } }'

# Windows
curl [...] https://localhost:9200/products/_search -d "{ \"query\": { \"match_all\": {} } }"
```

When sending data (typically JSON), we need to tell Elasticsearch which type of data we are sending. This 
can be done with the `Content-Type` HTTP header. Simply add it with cURL's `-H` argument.

```
curl -H "Content-Type:application/json" [...]
```

## Specifying the HTTP verb

You may also specify the HTTP verb (e.g. `POST`). This is necessary for some endpoints, such as when 
indexing documents. `GET` is assumed by default.

```
curl -X POST [...]
```

## All together now

```
# macOS & Linux
curl --cacert config/certs/http_ca.crt -u elastic https://localhost:9200/products/_search -d '{ "query": { "match_all": {} } }'

# Windows
curl --cacert config\certs\http_ca.crt -u elastic https://localhost:9200/products/_search -d "{ \"query\": { \"match_all\": {} } }"
```