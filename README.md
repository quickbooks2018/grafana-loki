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