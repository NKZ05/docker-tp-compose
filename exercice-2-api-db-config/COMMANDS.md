# COMMANDS for Exercice 2 — API + PostgreSQL (configuration via .env)
```
docker compose -f compose.yaml build
docker compose -f compose.yaml up -d
docker compose -f compose.yaml ps
docker compose -f compose.yaml logs -f
docker compose -f compose.yaml logs -f api
curl -sS http://localhost:3000/ | jq .
curl -sS http://localhost:3000/health | jq .
docker compose -f compose.yaml exec api sh
docker volume ls
docker volume inspect docker_tp_compose_ex2_db-data
docker compose -f compose.yaml down
docker compose -f compose.yaml down -v --rmi local --remove-orphans
docker volume rm docker_tp_compose_ex2_db-data
```