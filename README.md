# k8s-poc

## v2
### Feito

- Abortados o uso de arquivos Helm para subir os pods. Utilizado YAML.
- Provisionadas as apps:
1) Nginx Ingress
2) Prometheus
3) Grafana
- Serviços expostos para a web (kind: ingress)
1) Grafana: devopscheats.com
2) Prometheus: www.devopscheats.com
- Configurar redirect HTTPS para o Grafana

---

### A fazer no cluster self hosted:

- Configurar Alertmanager
- Configurar Grafana
- Configurar Node Exporter
>     https://devopscube.com/setup-prometheus-monitoring-on-kubernetes/

1) Alterar o runtime para containerd
2) prometheus-ingress: Configurar rewrite location / para /prometheus
3) grafana-ingress: Configurar rewrite location / para /grafana

- OK: prometheus-ingress: Habilitar a autenticação básica

### A fazer no AKS
- Configurar OAuth
>     https://kubernetes.github.io/ingress-nginx/examples/auth/oauth-external-auth/

---

## v1
* Foram usados arquivos yaml dos repositórios oficiais
* Nginx Ingress - tentativas de expor os serviços:
1) Foi possível configurar tanto VirtualServer quanto Ingress, porém os annotations não funcionam.

### Tasks v1 - DONE

Ao iniciar, execute:
> k apply -f nginx-ingress/11-service.yaml

Ao finalizar, execute:
> k delete -f nginx-ingress/11-service.yaml

- OK: Deployar o prometheus
- OK: Deployar o grafana
- OK: Prometheus: Corrigir coleta de metricas do kube-state-metrics e kubernetes-pods
- OK: Expor o Prometheus com ingress-nginx
- OK: Expor o Grafana com ingress-nginx
- OK: Configurar o Grafana com SSL
