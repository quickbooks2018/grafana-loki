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

- Loki
```bash
http://localhost:3100/metrics
```
