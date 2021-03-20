# helm-grafana

Example chart to install Grafana in your Kubernetes cluster

Chart Reference - https://github.com/grafana/helm-charts/tree/main/charts/grafana

|File|Description|
|--|--|
|configs/thanos-values.yaml | Sample config with Thanos Querier as datasource|

## Install/Upgrade Chart

Sample command to install (or) upgrade the chart -

```bash
helm upgrade -i grafana . -n platform --values=configs/thanos-values.yaml
```
