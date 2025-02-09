kubectl get secret/blue-elasticsearch-apm-server-apm-token -o go-template='{{index .data "secret-token" | base64decode}}' -n elk

pass: 9Q5sX8X16u13lxPYSu8ud58u

kubectl get secret blue-elasticsearch-es-elastic-user -o=jsonpath='{.data.elastic}' -n elk | base64 --decode; echo
user: elastic
pass: j6kUpK46996n2E17HU9rUotn

kibana: kubectl port-forward service/blue-kibana-kb-http  5601 -n elk
Elasticsearch: kubectl port-forward service/blue-elasticsearch-es-http  9200 -n elk

prometheus-operator: prometheus : kubectl --namespace monitoring port-forward svc/prometheus-k8s 9090
                     alert manager: kubectl --namespace monitoring port-forward svc/alertmanager-main 9093
                     grafana: kubectl --namespace monitoring port-forward svc/grafana 3000

QuestDB

kubectl port-forward service/questdb-single-local 31900:9000 -n questdb

GRAFANA

k port-forward service/grafana-service 3000:3000 -n grafana
default login: admin:admin

