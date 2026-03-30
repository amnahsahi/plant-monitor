# Smart Plant Monitoring System

A real-time plant monitoring application that tracks soil moisture, sends alerts when watering is needed, and visualises trends using Grafana.

---

## Overview

This project integrates soil moisture probes with a backend API to monitor plant health. Users can manage plants, receive notifications for low moisture levels, and view historical data through dashboards.

### Features
	•	Real-time soil moisture monitoring
	•	Alerts for low moisture levels
	•	Plant management (add, update, delete)
	•	REST API for data access
	•	Grafana dashboards for visualisation
	•	Docker-based deployment

### Tech Stack
	•	Backend: FastAPI
	•	Database: SQLite (plants.db)
	•	Frontend: Nginx
	•	Monitoring: Grafana
	•	Containerisation: Docker

### Architecture

```
┌────────────────────────────────────────────────────────┐
│                     Docker Network                     │
│                                                        │
│  ┌──────────┐    ┌──────────────┐    ┌──────────────┐  │
│  │ Frontend │    │   Backend    │    │   Grafana    │  │
│  │  Nginx   │───▶│   FastAPI    │    │  :3000       │  │
│  │  :3001   │    │   :8000      │    │              │  │
│  └──────────┘    │   SQLite DB  │◀───│ SQLite DS    │  │
│                  └──────────────┘    └──────────────┘  │
│                        ▲                               │
│                        │ POST /api/readings            │
│                  ┌─────┴──────┐                        │
│                  │   Probes   │                        │
│                  │ ESP32/Pico │                        │
│                  └────────────┘                        │
└────────────────────────────────────────────────────────┘
```
---
## Getting Started
git clone https://github.com/amnahsahi/plant-monitor.git
cd plant-monitor
docker-compose up --build

## Notes
	•	Database file: plants.db
	•	Configure environment variables via .env if required
	•	Grafana runs on port 3000 by default
