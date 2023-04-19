# Workshop - PersistentVolume & PersistentVolumeClaim


Para aplicar os manifestos em seu cluster, seguir os passos abaixo:
 
Em sua VM, criei um path com o seguinte comando para podermos atrelar ao k3d nos próximos passos.
```
mkdir -p /data/k3dvol
```

Criar cluster no k3d contendo um loadbalance com apontamento para o path /data para montar o volume.

Este comando criará um cluster chamado "bifrost-prd" com 2 workers e um load balancer que encaminha o tráfego da porta 80 do host para a porta 30000 do cluster.
O diretório "/data/k3dvol" no host será montado como um volume dentro do cluster no mesmo caminho.

Certifique-se de ter o K3d instalado e configurado antes de executar este comando. Além disso, observe que quanto mais workers você adicionar, mais recursos serão necessários para executar o cluster de forma eficiente. 
```
k3d cluster create bifrost-prd --agents 2 -p "80:30000@loadbalancer" --volume /data/k3dvol:/data/k3dvol
```

Caso queira apenas criar com um worker para teste, execute o comando abaixo.
```
k3d cluster create bifrost-prd -p "80:30000@loadbalancer" --volume /data/k3dvol:/data/k3dvol
```

Aplicar manifesto:
```
kubectl apply -f deployment-pvc.yml
```

Visualizar PersistentVolume & PersistentVolumeClaim:
```
kubectl get pv,pvc
```

Visualizar pod criado:
```
kubectl get pods
```

Abrir conexão com terminal interativo no container e validar o volume montado no path /data do container:
```
kubectl exec -it nomedopodcriado sh
df -h
```

Após acessar o container, iremos criar um arquivo para testar a persistência do volume, seguindo os seguinte passos abaixo!
```
Exibe o nome do seu host
echo $(hostname)
echo-7b7478b648-jkd8h

Cria um arquivo dentro do path com o nome do host
echo $(hostname) > /data/hostname.txt
exit
```

Após sair do container, execute o comando abaixo para visualizar o arquivo criado.
```
cat /data/k3dvol/hostname.txt
```

Observe o host em que o pod está sendo executado:
```
Visualiza o pod e em qual worker está sendo executado
kubectl get pods -o wide

valida nodes existente
kubectl get nodes -o wide
```

Agora iremos excluir o pod para validarmos a persistência.
```
kubectl delete pod/echo-7b7478b648-jkd8h
```

Aguarde até que o pod seja reprogramado novamente e verifique se o pod está sendo executado em um nó diferente.
```
kubectl get pods -o wide
```

Execute novamente o exec para acessar o novo pod.
```
kubectl exec -it echo-7b7478b648-98sbf sh
```

Valide se os dados são persistidos:
```
Exibe o nome do seu novo host
hostname
echo-7b7478b648-98sbf

Exibe o host do seu antigo container mapeado dentro do PVC 
cat /data/hostname.txt
echo-7b7478b648-jkd8h
```

Documentação Oficial do k3d e k8s sobre PV e PVC:
```
https://k3d.io/v5.4.9/

https://kubernetes.io/pt-br/docs/concepts/storage/persistent-volumes/
```
