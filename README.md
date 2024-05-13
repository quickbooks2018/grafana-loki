# Grafana Loki

- Docker Compose
```bash
docker compose -p loki -f docker-compose.yaml up -d
```

- Grafana
```bash
http://localhost:3000
user: admin
pass: secret
```

- In grafana, add Loki as a data source
```bash
http://loki:3100
```

- In grafana, add prometheus as a data source
```bash
http://prometheus:9090
```

- Loki
```bash
http://localhost:3100/metrics
```

- Import Dashboard
```bash
https://grafana.com/grafana/dashboards/13639-logs-app/
ID 13639
```

# Deploying Loki Stack on Kubernetes with Helm
```bash
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm repo ls
helm search repo grafana --versions
helm search repo grafana/loki-stack
helm search repo grafana/loki-stack --versions
helm show values grafana/loki-stack --version 2.10.2
helm show values grafana/loki-stack --version 2.10.2 > loki-stack-values.yaml
helm -n grafana-loki upgrade --install loki grafana/loki-stack --version 2.10.2 --create-namespace -f loki-stack-values.yaml --wait
```

- Grafana
```bash
kubectl port-forward -n grafana-loki service/loki-grafana 3000:80
user: admin
pass: see the password in the kubernetes secrets
```

- Note: loki promtail configuration is in the secrets with name loki-promtail 

- deploy a test pod to see the logs in grafana
```bash
k -n default run redis --image=redis:latest
k -n default run nginx --image=nginx:latest
```

- Grafana kubernetes Dashboard
```bash
https://grafana.com/grafana/dashboards/17781-loki-metrics-dashboard/
17781

Best for application logs
https://grafana.com/grafana/dashboards/15141-kubernetes-service-logs/
15141
```

- Navigate the grafana explore and see the logs of the redis pod and run queries