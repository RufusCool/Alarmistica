# Alarmistica

```
# Monitoramento - Prometheus e Grafana

Para aplicar os manifestos em seu cluster 
Acesse a raiz do repo e Execute:

```
Caso não possua ainda a NS monitoring criada, execute o comando abaixo para criar!

kubectl create namespace monitoring

Os comandos abaixo, irão aplicar os os manifestos.

kubectl create -f k8s-prometheus/clusterRole.yaml
kubectl create -f k8s-prometheus/config-map.yaml
kubectl create -f k8s-prometheus/prometheus-deployment.yaml 
kubectl create -f k8s-prometheus/prometheus-service.yaml --namespace=monitoring

kubectl apply -f kube-state-metrics/

kubectl create -f k8s-grafana/
```

Depois acesse http://192.168.1.10:32000/ (Grafana)

Usuario: admin

Senha: admin

Importe o dashboard do GrafanaLabs (https://grafana.com/grafana/dashboards/12740)

ID: 12740
