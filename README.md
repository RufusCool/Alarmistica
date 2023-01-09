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

Depois acesse http://grafana.192.168.15.43.nip.io/ (Grafana)

Usuario: admin

Senha: admin

K8S
Importe o dashboard do GrafanaLabs (https://grafana.com/grafana/dashboards/12740)
ID: 12740

MongoDB
Importe o dashboard do GrafanaLabs (https://grafana.com/grafana/dashboards/2583-mongodb/)
ID: 2583


```
kubectl create -f app-catalogo/

```


```
while true; do curl http://web.192.168.15.43.nip.io/produto; sleep 1; done;
```

EndPoints
```
Aplicação Catalogo
http://web.192.168.15.43.nip.io/produto
http://web.192.168.15.43.nip.io/swagger/index.html
http://web.192.168.15.43.nip.io/metrics

MongoDBExporter
http://exporter.192.168.15.43.nip.io/metrics

Grafana
http://grafana.192.168.15.43.nip.io/

Prometheus
http://prometheus.192.168.15.43.nip.io/


```



