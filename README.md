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
 
API key management is done in the web interface or using the Confluent Cloud commandline interface.

The credentials to work with a particular cluster are given by an API key and the related secret.
```
 export APIKEY_lkc-387om='KEY:SECRET'
```

## How to get a list of available metrics?
```
  http -v https://api.telemetry.confluent.cloud/v1/metrics/cloud/descriptors --auth $CCAccount > list_of_metrics.json
```

## How to query the metrics API?
```
  http -v https://api.telemetry.confluent.cloud/v1/metrics/cloud/attributes --auth $CCAccount < q1.json
```

## Which metrics are available via Confluent Cloud metrics API?

- io.confluent.kafka.server/received_bytes/delta
- io.confluent.kafka.server/sent_bytes/delta
- io.confluent.kafka.server/retained_bytes

## Query examples:

The official documentation provides some examples for retrieving aggregated metrics: https://docs.confluent.io/current/cloud/metrics-api.html.


