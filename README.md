# docker-compose-starters

Production-ready `docker-compose.yml` templates for common stacks.

**Copy. Configure `.env`. Run.**

No tutorials. No blog posts. Just working configs with health checks, named volumes, and sane defaults.

---

## Stacks

| Stack | Services | Folder |
|-------|----------|--------|
| PostgreSQL + Redis + pgAdmin | postgres:16, redis:7, pgadmin4 | `postgres-redis/` |
| FastAPI + PostgreSQL | fastapi, postgres:16, alembic | `fastapi-postgres/` |
| Node.js + PostgreSQL | node:20, postgres:16 | `node-postgres/` |
| Prometheus + Grafana | prometheus, grafana, node-exporter | `monitoring/` |

---

## Usage

```bash
git clone https://github.com/vipabdellahi-hash/docker-compose-starters
cd docker-compose-starters/postgres-redis

cp .env.example .env
# Edit .env — set passwords

docker compose up -d
```

---

## What's included in every stack

- ✅ Health checks on all services
- ✅ Named volumes (data survives restarts)
- ✅ `.env.example` with all required variables
- ✅ Resource limits
- ✅ Works on Linux, macOS, Windows (WSL2)
- ✅ No hardcoded secrets

---

## postgres-redis

```
postgres:16  ─── pgAdmin (port 5050)
redis:7      ─── password-protected, maxmemory set
```

```bash
cd postgres-redis
cp .env.example .env
docker compose up -d
# pgAdmin at http://localhost:5050
```

---

## fastapi-postgres

```
FastAPI app  ─── hot reload in dev
postgres:16  ─── health-checked
alembic      ─── runs migrations on startup
```

```bash
cd fastapi-postgres
cp .env.example .env
docker compose up -d
# API at http://localhost:8000
# Docs at http://localhost:8000/docs
```

---

## monitoring

```
Prometheus   ─── scrapes node-exporter
Grafana      ─── dashboards at port 3000
node-exporter─── host metrics
```

```bash
cd monitoring
cp .env.example .env
docker compose up -d
# Grafana at http://localhost:3000 (admin/admin)
```

---

## Contributing

Missing a stack you keep setting up manually? Open an issue.

---

## License

MIT
