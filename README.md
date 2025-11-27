# Ventilator


# Ventilator-get

Fuldt Docker-baseret miljø med MQTT, QuestDB, FastAPI, Flask, SPB-emulator og SPB-ingestor.

## Struktur

Alle services ligger i under-mapperne:
`api/`, `flask/`, `mosquitto/`, `questdb/`, `spb_emulator/`, `spb_ingestor/`, `loki/`.

Alle mapper indeholder kun konfiguration og kode. Ingen runtime-data følger med.

## Krav

Docker
Docker Compose v2

## Installation

Klon projektet:

```
git clone https://github.com/dbsk67060/Ventilator.git
cd Ventilator-get
```


Start hele systemet:

```
docker compose up -d
```

Systemet starter følgende services:
MQTT broker (Mosquitto)
QuestDB
FastAPI (backend)
Flask (dashboard)
SPB emulator
SPB ingestor
Loki
Promtail
Grafana

## Standardporte

MQTT: 1883
QuestDB UI: 9001
FastAPI: 18081
Flask: 15000
Grafana: 3000
Loki: 3100

## Konfiguration

Alle konfigurationsfiler er placeret i deres respektive mapper:
Mosquitto → `mosquitto/config/mosquitto.conf`
Loki → `loki/config.yaml`
Emulator og ingestor → egne `requirements.txt` og Python-filer.

Systemet bruger relative volumes. Docker opretter selv data-mapper når containerne starter.

## Opdatering

Træk seneste kode:

```
git pull
docker compose down
docker compose up -d --build
```

## Stop systemet

```
docker compose down
```

## Log-visning

```
docker compose logs -f
```

