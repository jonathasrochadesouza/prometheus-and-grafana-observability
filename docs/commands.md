# Commands

## Prerequisites

- Docker Engine 20.10+ and Docker Compose v2 plugin installed.
- Project `.env` created from `example.env` (Grafana admin credentials).

```bash
cp example.env .env
```

Validate setup before starting:

```bash
docker compose version && docker compose config
```

## Start services

Bring up Prometheus and Grafana in detached mode.

```bash
docker compose up -d
```

### Error handling

```bash
if ! docker compose up -d; then
  echo "Failed to start observability stack" >&2
  exit 1
fi
```

## Open in browser

Once services are healthy, open:

- **Grafana:** http://localhost:3000
- **Prometheus:** http://localhost:9090

## Stop services

```bash
docker compose stop
```

## Stop and remove containers, networks, and volumes

```bash
docker compose down
```

### Preserve data volumes

```bash
docker compose down --volumes
```

## View logs

Tail logs for all services:

```bash
docker compose logs -f
```

Follow a specific service (reduces noise and improves performance):

```bash
docker compose logs -f prometheus
docker compose logs -f grafana
```

### Error-resilient log streaming

```bash
docker compose logs -f --tail=100 grafana || echo "Grafana container not found or not running"
```

## Check service status

```bash
docker compose ps
```

## Restart a service

```bash
docker compose restart prometheus
```

## Troubleshooting

- **Port conflicts:** Ensure ports `9090` (Prometheus) and `3000` (Grafana) are available.
- **Missing credentials:** Verify `.env` exists and contains `grafana-user` and `grafana-password`.
- **Permission issues:** Check that `prometheus.yml` is readable by the container user.
