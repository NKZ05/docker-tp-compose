# COMMANDS for Exercice 1 — Premier service avec Docker Compose

```
docker compose -f compose.yaml build
docker compose -f compose.yaml up
docker compose -f compose.yaml up -d 
docker compose -f compose.yaml ps
docker compose -f compose.yaml logs -f
docker compose -f compose.yaml down --rmi local --volumes --remove-orphans
```