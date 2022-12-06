# Specific Changes for node-exporter out of k8s cluster
## Usage
### Run Cmd in Nodes to start Node-exporter

```console
wget https://github.com/prometheus/node_exporter/releases/download/v1.5.0/node_exporter-1.5.0.linux-amd64.tar.gz
tar xvfz node_exporter-*.*-amd64.tar.gz
cd node_exporter-*.*-amd64
./node_exporter
```
### modify values 
[values](./charts/kube-prometheus-stack/values.yaml) like below
```
prometheus-node-exporter:
  endpoints: ['10.10.10.184','10.10.10.102']
additionalScrapeConfigs:
  static_configs:
  - targets: ['10.10.10.184:9100','10.10.10.102:9100']

```

### build depenency and install
```console
cd charts
helm dependency build kube-prometheus-stack/
helm install prometheus -n prometheus kube-prometheus-stack/
```


# Prometheus Community Kubernetes Helm Charts ReadMe
[README](https://github.com/prometheus-community/helm-charts#readme)
