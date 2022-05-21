# K8S-PoC

## Single node

Por se tratar de um ambiente de PoC, vamos considerar que esta configuração será aplicada em um ambiente de Kubernetes Single Node.

Para evitar erro com *not tolerate taint*, execute o comando abaixo:

    kubectl taint nodes --all node-role.kubernetes.io/control-plane- node-role.kubernetes.io/master-

OPCIONAL:

Caso não tenha configurado um gerenciador de rede para o seu Kubernetes, você pode usar o Calico executando o comando abaixo:

    kubectl apply -f calico.yaml

Se for necessário fazer alguma alteração no pod CIDR, altere o range de IP na linha *4435*:

	 - name: CALICO_IPV4POOL_CIDR
       value: "10.142.0.0/24"

Para mais informações sobre a configuração do Calico, veja [Easy steps to install Calico CNI on Kubernetes Cluster | GoLinuxCloud](https://www.golinuxcloud.com/calico-kubernetes/)


### Ordem de configuração

Primeiramente, aplique as configurações do diretório *0-namespaces-secrets*:

    kubectl apply -f 0-namespaces-secrets/
 
Em seguida aplique as configurações dos demais:

    kubectl apply -f 1-ingress-nginx
    kubectl apply -f 2-monitoring/1_prometheus
    kubectl apply -f 2-monitoring/2_grafana
    kubectl apply -f 2-monitoring/3_kube-state-metrics
