# monitoring-for-confluent-cloud

## Prepare access to the Confluent Cloud systems
We have to use different credentials for accessing the Confluent Cloud in different contexts.

The different contexts are:

- manage clusters, topics, acls, etc.
- manage data flows into / via topics.

###
First, a login to the web based interface and also usage of ccloud CLI requires the Confluent Cloud account credentials.
With this, one can manage multiple environments and multiple clusters.
The CCAccount typically is based on an email address.

We export the credentials for the Confluent Cloud account as variable `CCAccount`.
```
 export CCAccount='USER:PASSWORD'
```

Access to each cluster can be granted by an API key.

API key management is done in the web interface or using the Confluent Cloud command line interface.

The credentials to work with a particular cluster are given by an API key and the related secret.
For the purpose of accessing the metrics API, one must create an API key for the cloud resource.
This can be done via
```bash
ccloud api-key create --resource cloud
```
Why it is also possible to authenticate using username and password, authentication using an API key is preferred since API keys can be rotated easily.
```
 export APIKEY_CLOUD='KEY:SECRET'
```

## How to get a list of available metrics?
```
  http -v https://api.telemetry.confluent.cloud/v1/metrics/cloud/descriptors --auth $APIKEY_CLOUD > list_of_metrics.json
```

## How to query the metrics API?
```
  http -v https://api.telemetry.confluent.cloud/v1/metrics/cloud/attributes --auth $APIKEY_CLOUD < q1.json
```

## Which metrics are available via Confluent Cloud metrics API?

- io.confluent.kafka.server/received_bytes/delta
- io.confluent.kafka.server/sent_bytes/delta
- io.confluent.kafka.server/retained_bytes

## Query examples:

The official documentation provides some examples for retrieving aggregated metrics: https://docs.confluent.io/current/cloud/metrics-api.html.
