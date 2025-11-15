# 🐄 Moo-ve-It! — Autonomous Smart Farm Ecosystem

Moo-ve-It! is a fully integrated smart-farm platform that combines **autonomous drones**, **IoT cow-tracking sensors**, and a **real-time monitoring web application** to enable next-generation herd management.
The ecosystem consists of three core components:

1. **Farm Monitoring App** — A real-time, browser-based farm visualizer with autonomous drone and herd simulation
2. **Backend API Server** — A Go-based REST API providing farm telemetry, drone/robo-dog status, and cow data
3. **ESP32 Cow Tracker Firmware** — IoT firmware for real cows, sending real-time telemetry to Sentry/backend systems

Together, these components demonstrate a modern, cloud-connected, autonomous livestock monitoring platform.

---

# 🚜 System Architecture

```
 ┌────────────────────┐        ┌────────────────────┐
 │ ESP32 Cow Trackers │──JSON──▶   Backend API      │
 │  (Real Cows)       │        │   (Go REST API)    │
 └────────────────────┘        └─────────┬──────────┘
                                         │
                                 Telemetry/Data
                                         │
                          ┌──────────────▼─────────────┐
                          │ Frontend Simulation App     │
                          │  (React + TS, SVG Map)      │
                          └─────────────────────────────┘
```

---

# 🌐 Project Components

## 1) Frontend — **Autonomous Herd Management Simulation**

*Source: React/TS + Tailwind + SVG Map*


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

## 2) Backend — **Go REST API for Smart Farm Telemetry**

*Source: Go 1.21*


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

## 3) IoT Firmware — **ESP32 Cow Tracking System**

*Source: Arduino / PlatformIO*


### ✨ Features

* AirTag-like positioning module integration
* Sends telemetry to Sentry.io / backend
* Smart WiFi auto-connect
* Low-power + reconnection handling
* Configurable reporting intervals

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

# 📂 Repository Structure (Suggested for Organization)

```
/moo-ve-it-org
│
├── frontend/         # React + TS simulation
├── backend/          # Go REST API
└── cow-firmware/     # ESP32 firmware
```

---

# 🚀 Get Started (Organization-Level)

Clone all modules:

```bash
git clone <org>/frontend
git clone <org>/backend
git clone <org>/cow-firmware
```

Run stack in order:

1. **Launch Backend**

   ```bash
   cd backend
   go run ./cmd/api
   ```

2. **Run Frontend**

   ```bash
   cd frontend
   python -m http.server 8000
   ```

3. **Deploy Trackers (Optional)**
   Flash ESP32 firmware from `cow-firmware`.

---

# 🤝 Contributing

We welcome PRs across all layers of the platform:

* UX / UI improvements
* Drone / herd behavioral algorithms
* API extensions
* Firmware optimizations
* Documentation & onboarding

---

# 📝 License

MIT Licensing applies to all components unless specified in sub-project READMEs.
