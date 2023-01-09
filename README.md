# Alarmistica


# Monitoramento - Prometheus -  Grafana e Zabbix

Para aplicar os manifestos em seu cluster acesse a raiz do repo e Execute:


```
Caso não possua ainda a NS monitoring criada, execute o comando abaixo para criar!

kubectl create namespace monitoring

Os comandos abaixo, irão aplicar os os manifestos.

kubectl create -f prometheus/clusterRole.yaml --namespace=monitoring
kubectl create -f prometheus/config-map.yaml --namespace=monitoring
kubectl create -f prometheus/prometheus-deployment.yaml --namespace=monitoring
kubectl create -f prometheus/prometheus-service.yaml --namespace=monitoring
kubectl create -f prometheus/prometheus-ingress.yaml --namespace=monitoring




kubectl create -f grafana/
```

Depois acesse http://192.168.1.10:32000/ (Grafana)

Usuario: admin

Senha: admin

Importe o dashboard do GrafanaLabs (https://grafana.com/grafana/dashboards/12740)

ID: 12740


```
kubectl create -f app-catalogo/

```
