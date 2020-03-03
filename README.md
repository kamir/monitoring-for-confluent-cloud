# monitoring-for-confluent-cloud

## Prepare access to the Confluent Cloud systems
We have to use different credentials for accessing the Confluent Cloud in different contexts.

First, a login to the web based interface requires the Confluent Cloud account credentials.
With this, one can manage multiple environments and multiple clusters.

We export the credentials for the Confluent Cloud account as variable C4.
```
 export CCAccount='USER:PASSWORD'
```

Access to each cluster can be granted by an API key. 
API key management is done in the web interface or using the Cconfluent Cloud commandline interface.

The credentials for a particular cluster are given by an API key and the related secret.
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

