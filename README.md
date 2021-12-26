# helm-grafana

Example chart to install Grafana in your Kubernetes cluster

Chart Reference - https://github.com/grafana/helm-charts/tree/main/charts/grafana

|File|Description|
|--|--|
|configs/thanos-values.yaml | Sample config with Thanos Querier as datasource|

## Pre-requisites

### Thanos Querier

Thanos querier is configured as a data source. This can be installed through https://github.com/HarshadRanganathan/helm-thanos

### Config Updates

1. Update `stages/prod/prod-values.yaml` file with appropriate values.

| | |
|--|--|
|alb.ingress.kubernetes.io/certificate-arn |ACM certificate ARN for TLS connection |
|alb.ingress.kubernetes.io/load-balancer-attributes |S3 bucket for writing LB logs |
|hosts |Hostname to which the ingress rules apply  |

## Install/Upgrade Chart

Sample command to install (or) upgrade the chart -

```bash
helm upgrade -i grafana . -n platform --values=stages/shared-values.yaml --values=stages/prod/prod-values.yaml
```

## Admin password

Get admin password by running this command:

```bash
kubectl get secret --namespace watcher grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```
