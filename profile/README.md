# 🐄 Moo-ve-It! — Autonomous Smart Farm Ecosystem

<p align="center">
  <img src="https://github.com/user-attachments/assets/ea9e3f82-5586-4578-99ff-ebf4539a8f3d" width="300">
</p>

Moo-ve-It! is a fully integrated smart-farm platform that combines **autonomous drones**, **IoT cow-tracking sensors**, and a **real-time monitoring web application** to enable next-generation herd management.
The ecosystem consists of three core components:

1. **Farm Monitoring App** — A real-time, browser-based farm visualizer with autonomous drone and herd simulation
2. **Backend API Server** — A Go-based REST API providing farm telemetry, drone/robo-dog status, and cow data
3. **ESP32 Cow Tracker Firmware** — IoT firmware for real cows, sending real-time telemetry to Sentry.io for processing by the backend

Together, these components demonstrate a modern, cloud-connected, autonomous livestock monitoring platform.

### Try the live system:

🌐 **Frontend Simulation:** [https://moo-ve-it.vercel.app](https://moo-ve-it.vercel.app)

🛰️ **Backend API (Live):** [https://backend-production-d9e3.up.railway.app/api/](https://backend-production-d9e3.up.railway.app/api/farm/state)...

---

# 🚜 System Architecture

<p align="center">
  <img src="https://github.com/user-attachments/assets/22006a47-8ed0-4e6d-be0a-875154a0c2cb">
</p>

---

# 🌐 Project Components

### 🗳️ Repositories

1. Cow tracker - https://github.com/Moo-ve-It/Cow-Tracker
2. Frontend - https://github.com/Moo-ve-It/frontend
3. Backend - https://github.com/Moo-ve-It/backend

## 1) IoT Firmware — **ESP32 Cow Tracking System**

*Source: Arduino / PlatformIO*

### ✨ Features

* Smart WiFi Connection - Automatically connects to strongest available network from configured list
* Air Tag Integration - Reads location data from air tag modules for real-time cow positioning
* Sentry.io Telemetry - Sends structured JSON events to Sentry.io at regular intervals
* Sensor Data Collection - Monitors battery level and optional environmental data
* Low Power Design - Optimized for battery-powered operation on livestock
* Network Resilience - Automatic reconnection handling for WiFi disruptions
* Configurable Reporting - Adjustable transmission intervals

### Data Sent (Example)

```json
{
  "device_id": "cow-001",
  "timestamp": 1700000000,
  "location": { "tag_id": "tag-abc123", "x": 45.2, "y": 78.5 },
  "battery_level": 87,
  "temperature": 22.5
}
```

### Setup

```bash
cp config.h.example config.h
# configure WiFi, device ID, Sentry credentials
```

---

## 2) Frontend — **Autonomous Herd Management Simulation**

[![Watch the video](https://img.youtube.com/vi/qSCKYaMRkXY/maxresdefault.jpg)](https://www.youtube.com/watch?v=qSCKYaMRkXY)

*Source: React/TS + Tailwind + SVG Map*

### 🌍 Live Demo

🔗 **[https://moo-ve-it.vercel.app](https://moo-ve-it.vercel.app)**

### ✨ Highlights

* Real-time drone & cattle simulation (30+ cows)
* Click-to-command drone navigation
* Interactive SVG farm map
* Autonomous drone AI: patrol, return-to-base, scanning
* Cow behavior modeling: leaders, followers, loners
* Dashboard: battery, weather, herd analytics, geofencing
* 100% client-side — no bundler needed (ES modules + importmap)

### Local Development

```bash
python -m http.server 8000
# or
serve .
```

Then open: `http://localhost:8000`.

---

## 3) Backend — **Go REST API for Smart Farm Telemetry**

*Source: Go 1.21*

### 🛰️ Live API

🔗 **Base URL:** [https://backend-production-d9e3.up.railway.app/api/](https://backend-production-d9e3.up.railway.app/api/farm/state)

### ✨ Features

* Farm-wide monitoring (cows, drone, robo-dog)
* Sensor-rich telemetry endpoints
* Health & metrics endpoints
* Structured JSON logging
* Modular clean architecture
* Railway deployment ready

### Key API Endpoints

```
GET /api/farm/state
GET /api/cows
GET /api/cows/:id
GET /api/robodog
GET /api/drone
GET /api/healthcheck
GET /api/debug/vars
```

### Run Locally

```bash
go mod download
go run ./cmd/api
```

Default port: **4000**

---

# 🧠 Unified Vision

Moo-ve-It! brings together robotics, IoT, and modern web technologies to prototype the future of digital agriculture:

* **Autonomous livestock management**
* **High-resolution real-time farm telemetry**
* **Battery-aware robotics (drone + robo-dog)**
* **AI-inspired herd behavior and simulation**
* **Cloud-ready infrastructure**

The system can be used for:

* Precision agriculture research
* Livestock safety monitoring
* Farm automation prototyping
* Hackathons & educational demos

---

# 📂 Repository Structure

```
/moo-ve-it-org
│
├── cow-firmware/     # ESP32 firmware
├── frontend/         # React + TS simulation
└── backend/          # Go REST API
```

---

# 📝 License

MIT Licensing applies to all components unless specified in sub-project READMEs.
