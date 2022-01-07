# k8s-poc

  Ao finalizar, execute:
    $ k delete -f nginx-ingress/11-service.yaml

  Para iniciar, execute:
    $ k apply -f nginx-ingress/11-service.yaml


Tasks:
- OK: Deployar o prometheus
- OK: Deployar o grafana
- OK: Prometheus: Corrigir coleta de metricas do kube-state-metrics e kubernetes-pods
- OK: Expor o Prometheus com ingress-nginx
- OK: Expor o Grafana com ingress-nginx
- OK: Configurar o Grafana com SSL

- Ativar HTTPS para o Grafana
- Configurar OAuth - https://kubernetes.github.io/ingress-nginx/examples/auth/oauth-external-auth/

- Alterar de subdominio (k8s-poc-prometheus.devopscheats.com) para URI (k8s-poc.devopscheats.com/prometheus)


- Configurar Alertmanager
- Configurar Grafana
- Configurar Node Exporter
https://devopscube.com/setup-prometheus-monitoring-on-kubernetes/


- Alterar o runtime para containerd