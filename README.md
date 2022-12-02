# Automate kubectl configmap update


**Configmap** A ConfigMap is an API object used to store non-confidential data in key-value pairs. 
Pods can consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a volume.

During development cycle there is manytimes requires to update the key-value pairs. The key-value pairs could be either in yaml or json format. 
Here is simple cli commands which can update the specific key-value pairs.

## Configmap updates

### Yaml format

1. ***Update a value in Prometheus metric configuration, say max and min shards***

```
kubectl get cm -n prom-ns prometheus-server -o yaml |  sed -e 's|max_shards: 1000|max_shards: 50|' | kubectl apply -f -
kubectl get cm -n prom-ns prometheus-server -o yaml |  sed -e 's|min_shards: 1|min_shards: 4|'     | kubectl apply -f -
```

### Json format

1. ***Update a value in Prometheus metric configuration, say max and min shards***

```
kubectl get cm -n prom-ns prometheus-server -o json |  sed -e 's|max_shards: 1000|max_shards: 50|' | kubectl apply -f -
kubectl get cm -n prom-ns prometheus-server -o json |  sed -e 's|min_shards: 1|min_shards: 4|'     | kubectl apply -f -
```

