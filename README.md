# IESL Wellhead Monitoring Pipeline

A real-time telemetry stack for monitoring wellhead assets — pressure, temperature, and flow rate. Built to mirror the kind of monitoring International Energy Services Limited runs in the field.

## Architecture

- **Mosquitto (MQTT)** | Lightweight broker — field sensors publish here |
- **Telegraf** | Subscribes to MQTT topics, parses the JSON, ships it to InfluxDB |
- **InfluxDB 2.7** | Time-series database — all that telemetry has to live somewhere |
- **Grafana** | Dashboards with proper oilfield units (psi, °F, barrels/day) |
- **Telegram Alerts** | Pings you when temp or pressure step out of line |

## How to Run
```bash
# Fire up the stack
docker compose up -d

# Start the sensor simulator
python3 scripts/sensor_simulator.py

# Kick off Telegram alerting (separate terminal)
python3 alerts/temp_alert.py
```

Grafana is at **http://localhost:3000** — login with default username and password (admin/admin)



























