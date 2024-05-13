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

- Loki
```bash
http://localhost:3100/metrics
```
