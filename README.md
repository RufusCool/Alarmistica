# Workshop - Monitoramento Prometheus e Grafana

Para aplicar os manifestos em seu cluster acesse a raiz do repo e Execute:


```
Caso não possua ainda a NS monitoring criada, execute o comando abaixo para criar!

kubectl create namespace monitoring

Os comandos abaixo, irão aplicar os manifestos.

kubectl create -f prometheus/

kubectl create -f grafana/

kubectl create -f app-catalogo/ 
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

Grafana
http://grafana.192.168.15.43.nip.io/

Prometheus
http://prometheus.192.168.15.43.nip.io/


```

Para aprimorar ainda mais seus estudos, consulte as documentações oficiais abaixo!
```
https://prometheus.io/
https://grafana.com/

```
