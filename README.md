# k8s-PoC

## Single node

Caso o seu ambiente PoC tenha apenas um Node, execute o comando abaixo para evitar o erro com *not tolerate taint*:

````kubectl taint nodes --all node-role.kubernetes.io/control-plane- node-role.kubernetes.io/master-````

## OPCIONAL:

Caso não tenha configurado um gerenciador de rede para o seu Kubernetes, você pode usar o Calico, que está neste repositório, executando o comando abaixo:

````kubectl apply -f calico.yaml````

Se for necessário fazer alguma alteração no pod CIDR, altere o range de IP na linha *4435*:

    - name: CALICO_IPV4POOL_CIDR
      value: "10.142.0.0/24"

Para mais informações sobre a configuração do Calico, veja [Easy steps to install Calico CNI on Kubernetes Cluster | GoLinuxCloud](https://www.golinuxcloud.com/calico-kubernetes/)


## Ordem de configuração

Primeiramente, aplique as configurações do diretório *0-namespaces-secrets*:

````kubectl apply -f namespaces-secrets/````
 
Em seguida aplique as configurações dos demais:

````kubectl apply -f namespaces/````    
````kubectl apply -f ingress-nginx/````    
````kubectl apply -f prometheus/````    
````kubectl apply -f grafana/````    
````kubectl apply -f kube-state-metrics/````    


> *OBS:* Ainda é necessário configurar o TLS nos ingress.
