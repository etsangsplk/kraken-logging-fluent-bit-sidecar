# Fluent-Bit Sidecar for Kubernetes

Run [Fluent-Bit](http://fluentbit.io/) as a sidecar to collect logs and output them to elasticsearch in a Kubernetes cluster. Fluent-Bit is configured in this example to tail a named directory (for the example: /mnt/log/reference-logging.txt) and collect all logs from the file.

This example includes a log generator app that runs with Fluent-Bit in one pod and writes logs to the named directory. 

## Bootstrap

To deploy in a Kubernetes cluster:

```kubectl -f create fluent-bit-sidecar.yaml```

[Elasticsearch for Kubernetes](https://github.com/kubernetes/kubernetes/tree/master/examples/elasticsearch)

## Plugins

#### Kubernetes Metadata Filter

This filter adds the following data into the body of the log.
* namespace
* pod id
* pod name
* labels
* host
* container name
* docker container id

For more information on the filter or to see a list of configuration options: http://fluentbit.io/documentation/0.11/filter/kubernetes.html