# Monitoramento - Prometheus

#### Deploy Prometheus 

Para subir a stack de Monitoramento no kubernetes 
Acesse a raiz do repositorio e Execute:

```
kubectl create namespace monitoring

kubectl create -f k8s-prometheus/clusterRole.yaml
kubectl create -f k8s-prometheus/config-map.yaml
kubectl create -f k8s-prometheus/prometheus-deployment.yaml 
kubectl create -f k8s-prometheus/prometheus-service.yaml --namespace=monitoring

##### Deploy kube-state-metrics

kubectl apply -f kube-state-metrics/

#### Deploy Grafana-Loki utilizando helm

helm repo add grafana https://grafana.github.io/helm-charts

helm install loki grafana/loki-stack --namespace monitoring --set grafana.enabled=false

kubectl patch svc loki --namespace=loki -p '{\"spec\": {\"ports\": [{\"port\": 3100,\"target-Port\": 3100}],\"type\": \"LoadBalancer\"}}'
