# COMMANDS for Exercice 3 — Front + API + Postgres (réseaux séparés)
```
docker compose -f compose.yaml build
docker compose -f compose.yaml up -d
docker compose -f compose.yaml ps
docker network ls
docker compose -f compose.yaml logs -f
docker compose -f compose.yaml logs -f api
curl -sS http://localhost:8080/api/health | jq .
curl -sS http://localhost:8080/api/message | jq .
docker compose -f compose.yaml exec api sh
docker compose -f compose.yaml down
docker compose -f compose.yaml down -v --rmi local --remove-orphans
docker compose -f compose.yaml ps
```