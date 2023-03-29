# Monitoramento - Prometheus

Para subir a stack de Monitoramento no kubernetes 
Acesse a raiz do repositorio e Execute:

```
kubectl create namespace monitoring

kubectl create -f k8s-prometheus/clusterRole.yaml
kubectl create -f k8s-prometheus/config-map.yaml
kubectl create -f k8s-prometheus/prometheus-deployment.yaml 
kubectl create -f k8s-prometheus/prometheus-service.yaml --namespace=monitoring

kubectl apply -f kube-state-metrics/
