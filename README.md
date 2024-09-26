# prometheus-helm-chart
Deploy Prometheus on a Kubernetes Cluster using Helm Chart

- Git clone this repository

- Create a prometheus namespace
```bash
kubectl create namespace prometheus
```

- Run this command to deploy Prometheus Helm Chart
```bash
helm install prometheus prometheus-community/prometheus -f custom-resources-prometheus.yaml --namespace prometheus
```

