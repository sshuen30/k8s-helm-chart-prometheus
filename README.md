# prometheus-helm-chart
Deploy Prometheus on a Kubernetes Cluster using Helm Chart

- Git clone this repository

- Create a prometheus namespace in the Kubernetes Cluster
```bash
kubectl create namespace prometheus
```

- Create a storageClass using nfs-subdir-ext provisioner
```bash
helm install nfs-subdir-external-provisioner-prometheus \
nfs-subdir-external-provisioner/nfs-subdir-external-provisioner \
--set nfs.server=172.16.44.32 \
--set nfs.path=/backup/prometheus \
--set storageClass.name=nfs-client-prometheus \
--set storageClass.onDelete=true \
--set clusterRole.create=true \
--set clusterRole.name=nfs-subdir-external-provisioner-prometheus \
--set clusterRoleBinding.create=true \
--set clusterRoleBinding.name=nfs-subdir-external-provisioner-binding-prometheus \
-n prometheus
```

- Run this command to deploy Prometheus Helm Chart
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install prometheus prometheus-community/prometheus -f custom-resources-prometheus.yaml --namespace prometheus
```

